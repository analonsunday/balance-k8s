# balance-k8s

Steps to deployment:

1. deploy microk8s using:
   snap install microk8s --classic --channel=1.20/stable
   microk8s.enable dns dashboard storage helm3 rbac
2. run: helm install balance charts/ -f charts/values.yaml
3. execute to allow ingress: helm install "ingress" ingress-nginx/ingress-nginx \ 
   --set tcp.8080="default/https-echo:8080" --set tcp.9090="default/prometheus:9090" \
   --set controller.hostNetwork=true \
   -f ingress.yaml
4. enjoy :)