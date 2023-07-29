## Create Both Deployments

* `kustomize build overlays/dev |   kubectl apply -f -`
  or in lower versions of k8s
* `kustomize build overlays/dev | KUBECTL_APPLYSET=true kubectl apply -f - --prune --applyset=sample --namespace default`


## Remove One Deployment
Comment out the deployment you don't want to deploy in 
* `base/kustomization.yaml` line `10` and `11`
  * ```
    # - path: deploymentB-dev.yaml
    # - path: serviceB-dev.yaml
    ``` 
* `overlays/dev/kustomization.yaml` line `10` and `11`
  * ```
    # - path: deploymentB-dev.yaml
    # - path: serviceB-dev.yaml
    ``` 

* prune the deployment you don't want to deploy
    * `kustomize build overlays/dev | KUBECTL_APPLYSET=true kubectl apply -f - --prune --applyset=sample --namespace default`