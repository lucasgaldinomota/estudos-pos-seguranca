# Minikube

🏗️ Minikube – Kubernetes Local para Desenvolvimento

O Minikube é uma ferramenta que permite rodar um cluster Kubernetes localmente, ideal para desenvolvimento e testes.

✔ Executa um cluster Kubernetes em uma VM ou contêiner 🖥️
✔ Compatível com Windows, macOS e Linux ✅
✔ Simula um ambiente Kubernetes real 🚀

⸻

1️⃣ Instalando o Minikube

📥 Linux

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

📥 macOS (Homebrew)

brew install minikube

📥 Windows (PowerShell)

choco install minikube



⸻

2️⃣ Inicializando um Cluster Minikube

minikube start

📌 Isso cria um cluster Kubernetes local usando um driver padrão (como Docker ou VirtualBox).

🔍 Verificar o Status

minikube status

🛑 Parar o Cluster

minikube stop

🔥 Deletar o Cluster

minikube delete



⸻

3️⃣ Usando o Kubectl com Minikube

O Minikube instala o kubectl automaticamente, então podemos usá-lo para gerenciar o cluster.

📦 Listar os Nós do Cluster

kubectl get nodes

🚀 Criar um Deployment

kubectl create deployment minha-app --image=nginx

🌐 Expor um Serviço

kubectl expose deployment minha-app --type=NodePort --port=80

🔗 Acessar a Aplicação

minikube service minha-app

Isso abre o serviço no navegador! 🌍

⸻

4️⃣ Configurações Avançadas

Escolher o Driver (Docker, VirtualBox, etc.)

minikube start --driver=docker

Aumentar Recursos (CPU/RAM)

minikube start --cpus=4 --memory=8192

Habilitar um Addon (ex: Ingress)

minikube addons enable ingress



⸻

5️⃣ Minikube vs. Kind vs. K3s

Ferramenta	Uso Principal	Vantagens
Minikube	Desenvolvimento Local	Fácil de instalar, roda em Docker/VM
Kind	Testes e CI/CD	Roda clusters Kubernetes dentro de contêineres
K3s	Kubernetes Leve	Ideal para IoT e Edge Computing

📌 Minikube é a melhor opção para iniciar com Kubernetes! 🚀

⸻

🔐 Conclusão

✔ Minikube facilita o desenvolvimento e testes em Kubernetes.
✔ Permite rodar um cluster Kubernetes local sem complicações.
✔ Fácil de integrar com Docker, Ingress, volumes e mais.

Se precisar de mais detalhes ou exemplos, me avise! 😊🚀