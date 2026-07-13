# 🚀 Passo a Passo para Executar a Solução Completa

## 1. Criar a pasta raiz dos microsserviços

Crie uma pasta que será utilizada para armazenar todos os repositórios que compõem a solução.

Exemplo:

```bash
mkdir Microsservicos
cd Microsservicos
```

---

## 2. Clonar os repositórios

Dentro da pasta `Microsservicos`, realize o clone dos 5 repositórios:

```bash
git clone <repositorio-orchestrator>

git clone <repositorio-users-api>

git clone <repositorio-catalog-api>

git clone <repositorio-payments-api>

git clone <repositorio-notifications-api>
```

Ao final, a estrutura dos diretórios deverá seguir o padrão:

```text
Microsservicos
│
├── Orchestrator
│
├── UsersApi
│
├── CatalogApi
│
├── PaymentsApi
│
└── NotificationsApi
```

---

## 3. Acessar o repositório Orchestrator

Entre na pasta responsável pela orquestração da solução:

```bash
cd Orchestrator
```

---

# 🐳 Executando com Docker Compose

## 4. Subir a arquitetura completa

Execute o comando:

```bash
docker compose up --build
```

Esse comando será responsável por:

- Criar as imagens Docker dos microsserviços.
- Criar a rede interna de comunicação entre os containers.
- Subir o RabbitMQ.
- Iniciar todos os microsserviços.
- Configurar a comunicação através das filas de eventos.

Os serviços iniciados serão:

- 👤 Users API
- 🎮 Catalog API
- 💳 Payments API
- 🔔 Notifications API
- 🐰 RabbitMQ

---

# ☸️ Executando utilizando Kubernetes

Além da execução utilizando **Docker Compose**, a solução também possui manifests Kubernetes para orquestração dos microsserviços.

Cada microsserviço possui seus próprios arquivos de configuração Kubernetes:

- Deployment
- Service
- ConfigMap
- Secret

Os manifests ficam organizados dentro de cada repositório:

Exemplo:

```text
UsersApi
└── Users.Api
    └── k8s
        ├── deployment.yaml
        ├── service.yaml
        ├── configmap.yaml
        └── secret.yaml
```

---

## 1. Aplicar os recursos Kubernetes

Cada microsserviço deve ser aplicado individualmente:

### Users API

```bash
kubectl apply -f UsersApi/Users.Api/k8s/
```

### Catalog API

```bash
kubectl apply -f CatalogApi/Catalog.Api/k8s/
```

### Payments API

```bash
kubectl apply -f PaymentsApi/Payments.Api/k8s/
```

### Notifications API

```bash
kubectl apply -f NotificationsApi/Notifications.Api/k8s/
```

---

## 🔍 Verificando os recursos Kubernetes

Verificar os pods:

```bash
kubectl get pods
```

Verificar os serviços:

```bash
kubectl get services
```

Verificar os deployments:

```bash
kubectl get deployments
```

Verificar os secrets:

```bash
kubectl get secrets
```

Verificar os configmaps:

```bash
kubectl get configmaps
```

---

# 🎯 Objetivo

O **Orchestrator** tem como objetivo simplificar a execução e gerenciamento da arquitetura completa de microsserviços, permitindo que todos os componentes sejam iniciados de forma integrada.

Este projeto demonstra conceitos importantes de arquitetura moderna:

- Arquitetura baseada em microsserviços.
- Comunicação assíncrona utilizando RabbitMQ.
- Containerização com Docker.
- Orquestração utilizando Kubernetes.
- Baixo acoplamento entre serviços.
- Escalabilidade e separação de responsabilidades.
