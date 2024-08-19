# KubePrometheus

## Preparando ambiente

```
git clone https://github.com/prometheus-operator/kube-prometheus

cd kube-prometheus

kubectl create -f manifests/setup

kubectl create -f manifests

kubectl get pods -n monitoring
```

## Mapenado localmente

```
kubectl get svc -n monitoring

kubectl port-forward -n monitoring svc/prometheus-k8s 9090:9090

kubectl port-forward -n monitoring svc/grafana 3000:3000
```