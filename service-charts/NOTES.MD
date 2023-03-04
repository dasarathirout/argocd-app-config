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
