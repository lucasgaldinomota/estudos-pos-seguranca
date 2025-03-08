# Docker API

A Docker API permite interagir com o Docker Daemon programaticamente usando chamadas HTTP. Ela é usada por ferramentas de orquestração, monitoramento e automação para gerenciar containers, imagens e redes.

⸻

1️⃣ Como Verificar se a Docker API Está Habilitada?

A Docker API está disponível localmente via socket UNIX em:

/var/run/docker.sock

Para verificar a versão da API:

curl --unix-socket /var/run/docker.sock http://localhost/version

Saída esperada:

{
  "Version": "24.0.2",
  "ApiVersion": "1.41",
  "MinAPIVersion": "1.12",
  "GitCommit": "a0bcc0b",
  "GoVersion": "go1.19.5"
}



⸻

2️⃣ Como Habilitar a API Remota com Segurança?

⚠ Nunca exponha a Docker API na rede sem autenticação.

Para habilitar a API via TCP com TLS:
1️⃣ Edite o arquivo de configuração do daemon

sudo nano /etc/docker/daemon.json

Adicione:

{
  "hosts": ["unix:///var/run/docker.sock", "tcp://0.0.0.0:2376"],
  "tls": true,
  "tlsverify": true,
  "tlscacert": "/etc/docker/ca.pem",
  "tlscert": "/etc/docker/server-cert.pem",
  "tlskey": "/etc/docker/server-key.pem"
}

2️⃣ Reinicie o Docker

sudo systemctl restart docker

Agora, a API pode ser acessada em https://<IP>:2376.

⸻

3️⃣ Como Usar a Docker API?

Você pode interagir com a API usando curl ou ferramentas HTTP.

📌 Listar Containers

curl --unix-socket /var/run/docker.sock http://localhost/containers/json

📌 Criar um Novo Container

curl --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" \
  -d '{"Image": "nginx", "Cmd": ["nginx", "-g", "daemon off;"]}' \
  http://localhost/containers/create

📌 Iniciar um Container

curl --unix-socket /var/run/docker.sock -X POST http://localhost/containers/<ID>/start

📌 Parar um Container

curl --unix-socket /var/run/docker.sock -X POST http://localhost/containers/<ID>/stop

📌 Excluir um Container

curl --unix-socket /var/run/docker.sock -X DELETE http://localhost/containers/<ID>



⸻

4️⃣ Protegendo a Docker API
	•	Use autenticação TLS para conexões remotas.
	•	Restringir acesso ao socket UNIX:

sudo chmod 660 /var/run/docker.sock
sudo usermod -aG docker $USER


	•	Bloqueie conexões externas via firewall:

sudo ufw deny 2375/tcp  # Porta insegura
sudo ufw allow 2376/tcp # Apenas se usar TLS



⸻

🔒 Conclusão

✔ A Docker API facilita o gerenciamento de containers remotamente.
✔ Nunca exponha a API sem autenticação TLS.
✔ Restringir acesso ao socket Docker melhora a segurança.

Se precisar de mais detalhes sobre autenticação ou integração com ferramentas, me avise! 🚀