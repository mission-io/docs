# Run Minikube

```
minikube start --container-runtime=cri-o  --bootstrapper=kubeadm --cpus=4 --memory=4096 --extra-config="apiserver.Authentication.TokenFile.TokenFile=$(pwd)/user-token.csv"
```
