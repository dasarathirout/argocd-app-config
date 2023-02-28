kubectl get all -n default
kubectl delete all --all -n default
kubectl get endpoints --namespace default
kubectl get services --all-namespaces
# INGRESS
helm upgrade --install ingress-nginx ingress-nginx --repo https://kubernetes.github.io/ingress-nginx --namespace default

# CHARTS TEMPLATES

helm template . -f environments\dev\conf.yaml --debug
helm uninstall local-run --debug
helm install local-run  . -f environments\dev\conf.yaml --debug --dry-run
helm install local-run  . -f environments\dev\conf.yaml --debug


#
admin
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
