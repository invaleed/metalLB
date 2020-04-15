# metalLB
Load balancer for baremetal k8s.

## Usage
```bash
$ git clone https://github.com/invaleed/metalLB.git
$ cd metalLB
$ kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.3/manifests/namespace.yaml
$ kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.3/manifests/metallb.yaml
```

Create secret
```bash
$ kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"
```

Apply configuration
```bash
$ kubectl apply -f configmap-metallb.yaml
```

Check metalLB pod and service
```bash
$ kubectl get pod,svc -n metallb-system
NAME                              READY   STATUS    RESTARTS   AGE
pod/controller-57f648cb96-5b8gt   1/1     Running   0          117m
pod/speaker-2w875                 1/1     Running   1          117m
pod/speaker-mcwpz                 1/1     Running   1          117m
pod/speaker-s6m89                 1/1     Running   0          117m
pod/speaker-ssrw2                 1/1     Running   0          117m
```
