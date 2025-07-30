# GitOps with ArgoCD

- This repository is for `argocd` manifests reference => add repo specific folders like `npx-app-manifests` and add manifests there.
- To install `argocd` on k8s cluster
  - Use below commands
    ```bash
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```
  - Install using the marketplace on cloud providers

- Port forwarding to access `argocd UI`
  ```bash
  kubectl port-forward svc/argocd-server -n argocd 8080:443
  ```
- On login dashboard username is `admin` for password use below commands
  ```bash
  kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
  ```
- As password is stored as **secret** by `argocd` hence it is `base64` encoded, to decode use below command
  ```bash
   echo "<encoded-string>" | base64 -d
  ```
- Once logged in create new application with your repository URL
