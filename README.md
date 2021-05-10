# strimzi-talk
Demo for strimzi talk


# Helm operator
```bash
helm repo add fluxcd https://charts.fluxcd.io
kubectl apply -f https://raw.githubusercontent.com/fluxcd/helm-operator/1.2.0/deploy/crds.yaml

helm upgrade -i helm-operator fluxcd/helm-operator \
    --namespace default \
    --set helm.versions=v3
```

# kafka namespace
```bash
kubectl create ns kafka
```

# deploy cluster

```bash
kubectl apply -f 01-operator-hr.yml
kubectl apply -f 02-kafka-cluster.yml
kubectl apply -f 03-kafka-topic.yml
kubectl apply -f 04-kowl.yml
```