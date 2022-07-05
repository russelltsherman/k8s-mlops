# README

## http ingress with minikube

create cluster
`make cluster`

apply blue whale app
`kubectl apply -f ./manifests/hello-blue-whale/hello-blue-whale.yaml`

apply blue whale http ingress
`kubectl apply -f ./manifests/hello-blue-whale/ingress.yaml`

edit /etc/hosts
`192.168.59.126  hello.minikube.local`

visit app page
`open http://hello.minikube.local/blue/`

## https ingress with mininkube

create cluster
`make cluster`

apply blue whale app
`kubectl apply -f ./manifests/hello-blue-whale/hello-blue-whale.yaml`

apply cert manager
`kubectl apply -f ./manifests/cert-manager/cert-manager.yaml`

apply cluster certificate issuer
`kubectl apply -f ./manifests/cert-manager/cluster-issuer.yaml`

apply blue whale https self-signed ingress
`kubectl apply -f ./manifests/hello-blue-whale/ingress.https.self-signed.yaml`

edit /etc/hosts
`192.168.59.126  self.secure.hello.minikube.local`

visit app page
`open https://self.secure.hello.minikube.local/blue/`

chrome presents certificate not trusted error
open system keychain, import certificate, mark as trusted.
`https://www.ateam-oracle.com/post/how-to-make-chrome-on-os-x-trust-a-self-signed-certificate`