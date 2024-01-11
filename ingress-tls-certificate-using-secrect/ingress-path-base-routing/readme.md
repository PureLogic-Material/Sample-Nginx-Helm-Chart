PART A Install the Nginx Ingress Controller
1 From the Cloud Shell, using kubectl, install the NGINX Ingress Controller components by using the public provider manifest:

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.2.1/deploy/static/provider/cloud/deploy.yaml

2 Confirm the controller is installed and running by viewing its deployment:

kubectl get deployments -n ingress-nginx

3 Find the external IP of Nginx:

kubectl get services -n ingress-nginx

Navigate to the IP address using a new browser tab. If you get an NGINX 404 Not Found error, everything is working fine. Nginx is up and running, but there are no Ingress objects, so no backend is found.


PART B Deploy the First Application and Ingress

Create the hello-app deployment:
kubectl create deployment hello-app --image=gcr.io/google-samples/hello-app:1.0

Expose the deployment:
kubectl expose deployment hello-app --port=8080 --target-port=8080

Click Open Editor.
vi ingress.yaml
kubectl apply -f ingress.yaml 


PART C Deploy the Second Application and Ingress
Create the whereami deployment:

kubectl create deployment whereami-app --image=gcr.io/google-samples/whereami:v1.1.1
Expose the deployment:

kubectl expose deployment whereami-app --port=8080 --target-port=8080
Return to the Cloud Editor tab.

Using the File menu, click New File.

Name your new file "whereami-ingress.yaml" and click OK.

kubectl apply -f whereami-ingress.yaml
