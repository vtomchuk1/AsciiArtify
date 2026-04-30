
# minikube

https://minikube.sigs.k8s.io/docs/start

```
minikube addons enable metrics-server

kubectl top node

kubectl top pod

kubectl top pod -A
```

**minikube demo**
![Image](doc/demo_minikube.gif)


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
![Image](doc/demo_kind.gif)


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
![Image](doc/demo_k3d.gif)
