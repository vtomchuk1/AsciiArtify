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
