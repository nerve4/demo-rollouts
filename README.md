# Demo-rollouts

## Summary

Argo Rollouts is a Kubernetes controller and set of CRDs which provide advanced deployment capabilities such as blue-green, canary, canary analysis, experimentation, and progressive delivery features to Kubernetes.


## Argo Rollouts Install

Standard installation:
```
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml
```

## Kubectl Plugin Installation

The kubectl plugin is optional, but is convenient for managing and visualizing rollouts from the command line.

Install Argo Rollouts Kubectl [plugin](https://github.com/argoproj/argo-rollouts/releases) with curl. 
```
curl -LO https://github.com/argoproj/argo-rollouts/releases/download/v1.5.0/kubectl-argo-rollouts-linux-amd64

chmod +x ./kubectl-argo-rollouts-linux-amd64

sudo mv ./kubectl-argo-rollouts-linux-amd64 /usr/local/bin/kubectl-argo-rollouts
```

Test to ensure the version you installed is up-to-date:
```
kubectl argo rollouts version
```
output something like this:
```
kubectl-argo-rollouts: v1.5.0+5b61b73
  BuildDate: 2023-05-05T19:58:54Z
  GitCommit: 5b61b73e6745eb285a8e25432a2ddb8175149da8
  GitTreeState: clean
  GoVersion: go1.19.9
  Compiler: gc
  Platform: linux/amd64
```

## Ingress Install

Make sure your nginx-ingress has been installed. Pods are:
```
kubectl get po -n ingress-nginx

NAME                                        READY   STATUS      RESTARTS      AGE
ingress-nginx-admission-create-d9ppx        0/1     Completed   0             3h22m
ingress-nginx-admission-patch-fwpgd         0/1     Completed   2             3h22m
ingress-nginx-controller-59575bdbf5-wwsx8   1/1     Running     1 (38m ago)   3h22m
```
Services are (make sure controller and contruller-admission are alive):
```
kubectl get svc -n ingress-nginx

NAME                                 TYPE           CLUSTER-IP     EXTERNAL-IP          PORT(S)                      AGE
ingress-nginx-controller             LoadBalancer   10.99.71.33    <YOUR-EXTERNAL-IP>   80:30885/TCP,443:31646/TCP   3h23m
ingress-nginx-controller-admission   ClusterIP      10.99.70.104   <none>               443/TCP                      3h23m
```

Examples have to be installed with additional `Ingress` object.
