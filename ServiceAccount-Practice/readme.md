kubectl config use-context acgk8s


kubectl create sa webautomation -n web


vi pod-reader.yml


kubectl create -f pod-reader.yml


vi rb-pod-reader.yml


kubectl create -f rb-pod-reader.yml


Testing the ServiceAccount....... 
kubectl get pods -n web --as=system:serviceaccount:web:webautomation

Note:
When we run below command it will run as admin so it will show the pods status...............
kubectl get pods -n web 
