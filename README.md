# k8s
![line](https://capsule-render.vercel.app/api?type=rect&color=gradient&height=1)
## install nginx-ingress with helm

> Documentation: https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-helm/

> add repository
```
helm repo add nginx-stable https://helm.nginx.com/stable
```
> update local helm chart repository cache
```
helm repo update
```
> install nginx-ingress
```
helm install ingress-nginx nginx-stable/nginx-ingress
```
![line](https://capsule-render.vercel.app/api?type=rect&color=gradient&height=1)
## install or upgrade ingress with helm
```
helm upgrade --install ingress-nginx ingress-nginx \
    --repo https://kubernetes.github.io/ingress-nginx \
    --namespace ingress-nginx --create-namespace
```
![line](https://capsule-render.vercel.app/api?type=rect&color=gradient&height=1)
## install cert-manager with helm

> Documentation: https://cert-manager.io/docs/installation/helm/

> add repository
```
helm repo add jetstack https://charts.jetstack.io
```

> install cert-manager with CRDs
```
helm install cert-manager jetstack/cert-manager \
    --namespace cert-manager \
    --create-namespace \
    --version v1.9.1 \
    --set installCRDs=true
```
![line](https://capsule-render.vercel.app/api?type=rect&color=gradient&height=1)
## install 1password/connect with helm

> add repository
```
helm repo add 1password https://1password.github.io/connect-helm-charts/
```
> add token
> Put our 1Password Connect access token in a variable
OP_TOKEN="< paste your token here >"

> Use Helm to install and configure everything. It will use the
> credential file and the ${OP_TOKEN} variable to use the integration
> we set up earlier.
### Upgrade 1password with helm
```
helm upgrade --install connect 1password/connect \
    --set-file connect.credentials=1password-credentials.json \
    --set operator.create=true \
    --set operator.token.value="${OP_TOKEN}" \
    --set "operator.watchNamespace={opconnect,pre-production}" --namespace opconnect # opconnect and production env
```
![line](https://capsule-render.vercel.app/api?type=rect&color=gradient&height=1)
