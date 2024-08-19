# Geral

## Instalação

- kind

Fonte: https://kind.sigs.k8s.io/docs/user/quick-start/#installation

```shell
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-amd64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
kind version
```

- kubectl

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

## Usando o kind

```
kind create cluster --config config.yml
kubectl version

kubectl get pod -A
kubectl get node
kubectl get pod -A -o wide
kubectl get node -v9

kubectl run --image nginx nginx
kubectl get pod -A -o wide
kubectl get pod -o wide
kubectl delete pod nginx
 
kubectl run --image nginx --dry-run -oyaml nginx > pod.yaml
kubectl get pod -o wide
kubectl apply -f pod.yaml 
kubectl get pod -o wide

kubectl create deployment --image nginx nginx
kubectl get pod -o wide
kubectl get deployment
kubectl get replicaset
kubectl scale deployment nginx --replicas 5
kubectl get replicaset
kubectl get deployment
kubectl get pod -o wide
kubectl delete deploy nginx

kubectl create deployment --image nginx --dry-run=client -oyaml nginx > deployment.yaml
kubectl get pod -o wide
kubectl get deployment
kubectl apply -f deployment.yaml 
kubectl get pod -o wide

kubectl create deployment --image mateusmuller2/webserver --dry-run=client -oyaml webserver > deployment-webserver.yaml
kubectl apply -f deployment-webserver.yaml 
kubectl get pod -o wide
kubectl get deployment
kubectl delete deploy webserver
kubectl get pod -o wide
kubectl apply -f deployment-webserver.yaml 
kubectl get pod -o widecluster

kubectl run --image alpine -it demo sh
apk install curl
curl 10.244.3.7
kubectl expose deployment webserver --port 80 --target-port 80

kubectl get service -oyaml > service.yaml
kubectl get pod --show-labels
kubectl get endpoints webserver
curl http://webserver.default.svc.cluster.local

#alternando o pod, devido o load balance
while true; do curl http://webserver.default.svc.cluster.local; done
```
