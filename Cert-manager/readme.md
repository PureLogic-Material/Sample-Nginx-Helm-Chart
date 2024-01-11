kubectl get service -n accounts


openssl req -nodes -new -x509 -keyout accounts.key -out accounts.crt -subj "/CN=hello-app.svc"

//2nd method to generate key and certificate using DNS.......... 
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ingress.key -out ingress.crt -subj "/CN="DNS-Name"=ingress"
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ingress.key -out ingress.crt -subj "/CN="c1-dns-ozzr7srn.hcp.eastus.azmk8s.io"=ingress"
vi accounts-tls-certs-secret.yml


base64 accounts.crt


vi secret.yml
//Under tls.crt:, replace the placeholder text with the copied Base64-encoded string output.


base64 accounts.key
vi secret.yml
//Enter the command :set paste and i to enter insert mode.


kubectl create -f secret.yml

vi accounts-tls-ingress.yml
kubectl create -f accounts-tls-ingress.yml
kubectl describe ingress accounts-tls -n accounts

curl -v -k "URL"

detail Blog links	...........
using issuer
https://mrdevops.medium.com/secure-your-aks-ingress-with-letsencrypt-and-cert-manager-97a698418cf3
https://cert-manager.io/docs/tutorials/getting-started-aks-letsencrypt/
