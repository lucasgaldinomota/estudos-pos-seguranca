# Docker Daemon

O Docker Daemon (dockerd) é o processo que gerencia containers, redes, volumes e imagens no Docker. Ele roda como um serviço no sistema operacional e escuta comandos do CLI (docker) ou de APIs externas.

⚠️ Por que proteger o Docker Daemon?
	•	Acesso irrestrito ao Docker Daemon permite controle total sobre o host.
	•	Exploração de vulnerabilidades pode levar a ataques em escala.
	•	Configuração insegura pode permitir execução de containers com privilégios elevados.

⸻

1️⃣ Configuração Segura do Docker Daemon

Verifique o Status do Docker Daemon

systemctl status docker

Se estiver ativo, ele pode ser configurado no arquivo /etc/docker/daemon.json.

Edite o Arquivo de Configuração

Crie ou edite /etc/docker/daemon.json para reforçar a segurança:

{
  "icc": false,
  "userns-remap": "default",
  "no-new-privileges": true,
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  },
  "live-restore": true,
  "experimental": false,
  "tls": true,
  "tlsverify": true,
  "tlscacert": "/etc/docker/ca.pem",
  "tlscert": "/etc/docker/server-cert.pem",
  "tlskey": "/etc/docker/server-key.pem",
  "group": "docker"
}

📌 Explicação:
	•	"icc": false" → Bloqueia comunicação entre containers sem regras explícitas.
	•	"userns-remap": "default" → Ativa User Namespaces para isolar usuários do host.
	•	"no-new-privileges": true" → Impede que processos aumentem privilégios.
	•	"log-driver": "json-file" → Configura logs seguros para evitar logs infinitos.
	•	"live-restore": true" → Mantém containers rodando após reinício do daemon.
	•	"experimental": false" → Desativa recursos experimentais para evitar vulnerabilidades.
	•	TLS ativado → Protege comunicação remota com autenticação segura.

Reinicie o Docker para Aplicar as Configurações

sudo systemctl restart docker



⸻

2️⃣ Proteção do Socket do Docker

Por padrão, o Docker Daemon escuta no socket /var/run/docker.sock, permitindo acesso total ao sistema.

Restrinja Permissões do Socket

sudo chmod 660 /var/run/docker.sock
sudo usermod -aG docker $USER

🔹 Apenas usuários do grupo docker podem acessar o daemon.

⸻

3️⃣ Evite Exposição Remota do Docker Daemon

Por padrão, o daemon escuta localmente. Evite expô-lo na rede, pois isso dá acesso remoto ao Docker sem autenticação.

❌ Exposição Insegura (NÃO FAÇA)

sudo dockerd -H tcp://0.0.0.0:2375

Isso permite que qualquer pessoa na rede controle seus containers! 🚨

✅ Exposição Segura com TLS

Se precisar acessar remotamente, habilite TLS:

sudo dockerd --tlsverify \
  --tlscacert=/etc/docker/ca.pem \
  --tlscert=/etc/docker/server-cert.pem \
  --tlskey=/etc/docker/server-key.pem \
  -H=0.0.0.0:2376

Agora, apenas clientes autenticados podem se conectar.

⸻

4️⃣ Limitação de Recursos

Restrinja Recursos Usados pelo Daemon

Adicione ao daemon.json:

{
  "default-shm-size": "64m",
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "50m",
    "max-file": "5"
  },
  "storage-driver": "overlay2"
}

🔹 Explicação:
	•	"default-shm-size": "64m" → Limita o uso de memória compartilhada.
	•	"log-driver": "json-file" → Define logs seguros.
	•	"storage-driver": "overlay2" → Usa um driver de armazenamento eficiente.

⸻

5️⃣ Monitoramento e Auditoria

Verifique Logs do Docker

journalctl -u docker --no-pager | tail -n 50

Use Ferramentas de Segurança
	•	Docker Bench for Security (verifica configurações inseguras)

docker run --rm --net host --pid host --userns host --cap-add audit_control \
-e DOCKER_CONTENT_TRUST=1 aquasec/docker-bench-security


	•	Falco (detecta ameaças em tempo real)

falco -r /etc/falco/falco_rules.yaml



⸻

🔒 Resumo das Boas Práticas

✅ Nunca exponha o Docker Daemon na rede sem TLS
✅ Restrinja acesso ao socket /var/run/docker.sock
✅ Use userns-remap para isolar containers do host
✅ Habilite logs e limites de memória no daemon.json
✅ Monitore atividades suspeitas com Falco e Docker Bench

Seguindo essas práticas, o Docker Daemon fica muito mais seguro! 🚀 Alguma dúvida ou algo que queira aprofundar?