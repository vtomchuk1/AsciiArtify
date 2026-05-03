## Minikube vs. k3d vs. kind comparing table

|  | Minikube | k3d | kind
|--|--|--|--|
| Developer | Kubernetes SIG | CNCF _(Rancher)_ | Kubernetes SIG |
| Installation complexity | 1/5 | 3/5 | 1/5 |
| Creating a cluster | minikube start | k3d  cluster  create | kind create cluster |
| Popularity | 1st | 2nd | 3rd |
| Performance | 3rd | 1st | 2nd |
| Cluster resource consumptions | 3rd | 1st | 2nd |
| Compatibility | Windows, macOS, Linux | Windows, macOS, Linux | Windows, macOS, Linux |

Comparing Minikube, kind, and k3d
Minikube is the official local Kubernetes release. It is part of Kubernetes; it's very mature and very full featured. That said, it requires a VM and is both slow to install and to start. It can also get into trouble with networking at arbitrary times and sometimes the only remedy is deleting the cluster and rebooting. Also, Minikube supports a single node only. I suggest using Minikube only if it supports some feature that you need that is not available in either kind or k3d.

kind is much faster than Minikube and is used for Kubernetes conformance tests, so by definition, it is a conformant Kubernetes distribution. It is the only local cluster solution that provides HA clusters with multiple control-plane nodes. It is also designed to be used as a library, which I don't find as a big attraction because it is very easy to automate CLIs from code. The main downside of KinD for local development is that it is ephemeral. I recommend using kind if you contribute to Kubernetes itself and want to test against it.

k3d is the clear winner. It's lightning fast, supports multiple clusters, and supports multiple worker nodes per cluster. It's also easy to stop and start clusters without losing state.


# minikube

https://minikube.sigs.k8s.io/docs/start

```
minikube addons enable metrics-server

kubectl top node

kubectl top pod

kubectl top pod -A
```

**minikube demo**
![Image](demo_minikube.gif)


# kind

https://kind.sigs.k8s.io/docs/user/quick-start/#creating-a-cluster

```
kind create cluster --name hello-kind

kubectl cluster-info --context kind-hello-kind

kind get clusters

kubectl get pods

kubectl port-forward pod/hello-world 8081:8080

kubectl describe pod hello-world

kubectl get all

kubectl expose pod hello-world --port=8080 --name=hello-svc

kubectl run curl-test --rm -it --image=curlimages/curl -- curl -s http://hello-svc:8080
```

**kind demo**
![Image](demo_kind.gif)


# k3d

```
k3d cluster create helloworld

kubectl get nodes

kubectl run hello-world --image=gcr.io/google-samples/hello-app:1.0 --port=8080

kubectl get pods

kubectl port-forward pod/hello-world 8081:8080 > /dev/null 2>&1 &

curl http://localhost:8081

kill $!
```

**k3d demo**
![Image](demo_k3d.gif)
