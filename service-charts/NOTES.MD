# kubectl delete all --all --all-namespaces
kubectl get all -n default
kubectl delete all --all -n default
kubectl get endpoints --namespace default
kubectl get services --all-namespaces
# INGRESS
helm upgrade --install ingress-nginx ingress-nginx --repo https://kubernetes.github.io/ingress-nginx --namespace default

# CHARTS TEMPLATES
helm list --all --all-namespaces
helm template . -f environments\dev\conf.yaml --debug
helm uninstall k8s-drout-run --debug
helm install k8s-drout-run  . -f environments\dev\conf.yaml --debug --dry-run
helm install k8s-drout-run  . -f environments\dev\conf.yaml --debug
helm upgrade k8s-drout-run --atomic --debug --install --force . -f environments\dev\conf.yaml 


#
admin
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.6.4/deploy/static/provider/cloud/deploy.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

