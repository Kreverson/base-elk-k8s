# Repositório base da stack ELK (Elasticsearch, Filebeat, Kibana)

Nesse passo a passo, vamos aplicar no cluster Kubernetes a estrutura básica para coletar logs de aplicações utilizando a stack ELK.

## Requisitos

1. Docker Desktop (on Mac & Windows) ou Docker Engine (on Linux)
2. Kubectl
3. Minikube

## Verificar requisitos

```sh
docker --version
```

```sh
kubectl version --client
```

```sh
minikube version
```

## Iniciar o cluster do minikube

```sh
minikube start --cpus=4 --memory=4096 --driver=docker
```

```sh
kubectl get nodes
```

## Subir as aplicações exemplo no namespace demo-apps que gerarão os logs

```sh
kubectl create namespace demo-apps
```

```sh
kubectl apply -f app1.yaml
```

```sh
kubectl apply -f app2.yaml
```

## Subir o Elasticsearch no namespace logging (localmente/minikube)
A diferença está no provisionamento do volume.

```sh
kubectl create namespace logging
```
```sh
kubectl apply -f local-elasticsearch-pv.yaml
```
```sh
kubectl apply -f local-elasticsearch.yaml
```

## Subir o Elasticsearch no namespace logging (AWS (EKS), GKE ou AKS)
A diferença está no provisionamento do volume.

```sh
kubectl create namespace logging
```
```sh
kubectl apply -f prd-elasticsearch.yaml
```

### Verificar Elasticsearch Pod & PVC
```sh
kubectl get pods -n logging
```
```sh
kubectl describe pod <pod-name> -n logging
```

```sh
kubectl get pvc -n logging
```
```sh
kubectl get pv -n logging
```