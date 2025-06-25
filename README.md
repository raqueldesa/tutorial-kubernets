# tutorial-kubernets

Este é um projeto inicial para estudo de Kubernetes e clusterização, desenvolvido como parte da disciplina de **Gerência de Configuração** da UFAM.

## Descrição

O projeto demonstra como criar e orquestrar uma aplicação web simples com MongoDB utilizando recursos básicos do Kubernetes, incluindo:

- Deployments
- Services (ClusterIP e NodePort)
- Secrets e ConfigMaps para gerenciamento de variáveis sensíveis e de configuração

## Estrutura
- `mongo-config.yaml`: Configurações (como URLs, nomes de serviços, etc.) nos pods sem precisar alterar a imagem do container.
- `mongo-secret.yaml`: Secret com usuário e senha do MongoDB (em base64)
- `mongo.yaml`: Deployment e Service para o banco de dados MongoDB
- `webapp.yaml`: Deployment e Service para a aplicação web que consome o MongoDB

## Pré-requisitos

- Ter minikube instalado -> [Guia de instalação Kubernets](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download)
- Ter docker instalado ->  [Guia de instalação Docker - Windows](https://docs.docker.com/desktop/setup/install/windows-install/) 
- Kubernetes (Minikube, Docker Desktop ou outro cluster local)
- kubectl

## Como usar

1. **Clone o repositório**
2. **Aplique os manifests na ordem:**
   
   ```sh
   kubectl apply -f mongo-config.yaml
   kubectl apply -f mongo-secret.yaml
   kubectl apply -f mongo.yaml
   kubectl apply -f webapp.yaml
   ```
   
4. **Acesse a aplicação**
   
   - Se estiver usando Minikube. Este comando cria um túnel (proxy) que redireciona o tráfego do seu localhost para o serviço dentro do cluster.
     ```sh
     minikube service webapp-service
     ```
   - Ou acesse via `http://<ip-minikube>:<nodePort>` conforme configurado no seu serviço. Este comando retorna o ip do minikube
     ```sh
     minikube ip
     ```


## Referências

- [Documentação oficial do Kubernetes](https://kubernetes.io/docs/)
- [Tutorial Kubernetes da Nana Janashia](https://www.youtube.com/c/TechWorldwithNana)
- [Documentação do Minikube](https://minikube.sigs.k8s.io/docs/)
- [Documentação do MongoDB Docker](https://hub.docker.com/_/mongo)

---
Projeto para fins didáticos na disciplina de Gerência de Configuração — UFAM.
