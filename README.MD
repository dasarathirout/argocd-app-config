# Windows CLI Commands ArgoCD


## Install
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


C:\Users\RDasarathi>k get ns
NAME              STATUS   AGE
argocd            Active   49m
default           Active   51m
kube-node-lease   Active   51m
kube-public       Active   51m
kube-system       Active   51m

C:\Users\RDasarathi>k -n argocd get deployment
NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
argocd-applicationset-controller   1/1     1            1           54m
argocd-dex-server                  1/1     1            1           54m
argocd-notifications-controller    1/1     1            1           54m
argocd-redis                       1/1     1            1           54m
argocd-repo-server                 1/1     1            1           54m
argocd-server                      1/1     1            1           54m

C:\Users\RDasarathi>k -n argocd  get pods
NAME                                                READY   STATUS    RESTARTS   AGE
argocd-application-controller-0                     1/1     Running   0          47m
argocd-applicationset-controller-6676c4d655-cxdlh   1/1     Running   0          47m
argocd-dex-server-5f9bd56758-qjlzg                  1/1     Running   0          47m
argocd-notifications-controller-5bc766fc6d-jgvv6    1/1     Running   0          47m
argocd-redis-6fd7cbd95d-nvnlf                       1/1     Running   0          47m
argocd-repo-server-5bb545d667-2b6cz                 1/1     Running   0          47m
argocd-server-6b88fbcbb8-8bms9                      1/1     Running   0          47m

C:\Users\RDasarathi>k -n argocd  get services
NAME                                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
argocd-applicationset-controller          ClusterIP   10.104.132.136   <none>        7000/TCP,8080/TCP            48m
argocd-dex-server                         ClusterIP   10.107.180.0     <none>        5556/TCP,5557/TCP,5558/TCP   48m
argocd-metrics                            ClusterIP   10.102.102.202   <none>        8082/TCP                     48m
argocd-notifications-controller-metrics   ClusterIP   10.96.42.228     <none>        9001/TCP                     48m
argocd-redis                              ClusterIP   10.106.210.157   <none>        6379/TCP                     48m
argocd-repo-server                        ClusterIP   10.109.216.253   <none>        8081/TCP,8084/TCP            48m
argocd-server                             ClusterIP   10.103.149.126   <none>        80/TCP,443/TCP               48m
argocd-server-metrics                     ClusterIP   10.111.28.224    <none>        8083/TCP                     48m

C:\Users\RDasarathi>k -n argocd  get secrets
NAME                          TYPE     DATA   AGE
argocd-initial-admin-secret   Opaque   1      46m
argocd-notifications-secret   Opaque   0      48m
argocd-secret                 Opaque   5      48m

C:\Users\RDasarathi>k -n argocd  get configmaps
NAME                        DATA   AGE
argocd-cm                   0      48m
argocd-cmd-params-cm        0      48m
argocd-gpg-keys-cm          0      48m
argocd-notifications-cm     0      48m
argocd-rbac-cm              0      48m
argocd-ssh-known-hosts-cm   1      48m
argocd-tls-certs-cm         0      48m
kube-root-ca.crt            1      48m


C:\Users\RDasarathi>k -n argocd get deployment
NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
argocd-applicationset-controller   1/1     1            1           54m
argocd-dex-server                  1/1     1            1           54m
argocd-notifications-controller    1/1     1            1           54m
argocd-redis                       1/1     1            1           54m
argocd-repo-server                 1/1     1            1           54m
argocd-server                      1/1     1            1           54m


## Portforward UI
C:\Users\RDasarathi>

kubectl -n argocd port-forward svc/argocd-server -n argocd 8080:443

## Login Creds
GIT-BASH> kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
admin/ OUCFfZpFJooiiXWc


docker pull nginx/nginx:1.23.1
docker pull kong/kubernetes-ingress-controller:2.7.0