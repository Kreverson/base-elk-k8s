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
