# Configuração Segura do Docker

Configurar o Docker de forma segura é essencial para evitar ataques e vazamentos de dados. Aqui estão as melhores práticas para fortalecer a segurança do Docker:

⸻

1. Instalação e Manutenção Segura

✅ Mantenha o Docker Atualizado
	•	Use a versão mais recente do Docker para obter patches de segurança.
	•	Atualize regularmente com:

sudo apt update && sudo apt upgrade docker-ce -y



✅ Verifique a Integridade do Binário
	•	Baixe o Docker apenas de fontes oficiais.
	•	Confirme a assinatura GPG antes da instalação:

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg



⸻

2. Configuração do Daemon com Segurança

O daemon do Docker roda com privilégios elevados, então é crucial restringir seu acesso.

✅ Evite Expor o Daemon Remotamente
	•	Nunca exponha o Docker daemon na rede sem segurança. Se for necessário, use TLS:

sudo dockerd --tlsverify --tlscacert=/etc/docker/ca.pem --tlscert=/etc/docker/server-cert.pem --tlskey=/etc/docker/server-key.pem -H=0.0.0.0:2376



✅ Configure o Daemon com um Perfil Seguro
	•	Crie um arquivo /etc/docker/daemon.json com:

{
  "icc": false,
  "userns-remap": "default",
  "no-new-privileges": true,
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  }
}

🔹 Explicação:
	•	"icc": false → Impede que containers se comuniquem sem regras explícitas.
	•	"userns-remap": "default" → Habilita User Namespaces para isolar containers.
	•	"no-new-privileges": true → Evita escalonamento de privilégios.
	•	"log-driver": "json-file" → Configura logging seguro.

✅ Restrinja Permissões no Socket do Docker
	•	O socket /var/run/docker.sock permite controle total sobre o host, então:

sudo chmod 660 /var/run/docker.sock
sudo usermod -aG docker <seu-usuario>



⸻

3. Segurança na Execução de Containers

✅ Execute Containers como Usuário Não Root
	•	Evite executar containers como root, criando um usuário específico:

FROM alpine
RUN adduser -D appuser
USER appuser

Ou ao rodar o container:

docker run --user 1001 alpine



✅ Evite o Modo Privilegiado (--privileged)
	•	Containers privilegiados têm acesso irrestrito ao host.
❌ NUNCA use:

docker run --privileged ...



✅ Restringir Recursos com cgroups e seccomp
	•	Defina limites para evitar ataques de negação de serviço (DoS):

docker run --memory=512m --cpus="1.0" ubuntu


	•	Ative o modo seguro do kernel (seccomp):

docker run --security-opt seccomp=default.json ubuntu



✅ Evite Montar o Filesystem do Host
❌ Evite permitir acesso irrestrito ao host:

docker run -v /:/host-root ubuntu

🔹 Isso dá ao container controle total sobre o sistema!

✅ Use Capabilities Mínimas
	•	Remova capacidades desnecessárias com --cap-drop:

docker run --cap-drop ALL --cap-add NET_BIND_SERVICE nginx



⸻

4. Segurança na Rede

✅ Desative o Modo --network=host
	•	Containers usando --network=host compartilham a rede do host, o que pode ser explorado.
	•	Prefira redes bridge ou overlay para isolar containers.

✅ Habilite iptables para Controle de Rede
	•	Configure regras de firewall para restringir comunicação:

sudo iptables -A FORWARD -i docker0 -o eth0 -j DROP



✅ Use Redes Customizadas
	•	Defina redes separadas para cada serviço:

docker network create --driver bridge secure_network
docker run --network secure_network nginx



⸻

5. Segurança no Armazenamento

✅ Use Volumes ao Invés de Bind Mounts
	•	Evite expor arquivos sensíveis com -v /etc:/host-etc.
	•	Prefira volumes gerenciados pelo Docker:

docker volume create meu_volume
docker run -v meu_volume:/app/data alpine



✅ Proteja Dados Sensíveis
	•	Use secrets para armazenar senhas e chaves:

echo "senha-secreta" | docker secret create minha_senha -
docker service create --secret minha_senha nginx



⸻

6. Monitoramento e Auditoria

✅ Ative Logging para Containers e Daemon
	•	Visualize logs:

docker logs <container_id>


	•	Configure logs estruturados:

{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "50m",
    "max-file": "5"
  }
}



✅ Use Ferramentas de Monitoramento
	•	Falco para detectar comportamentos suspeitos:

falco -r /etc/falco/falco_rules.yaml -K /etc/falco/falco.key


	•	Sysdig para monitoramento forense:

sysdig -c echo_fds



✅ Verifique a Segurança Periodicamente
	•	Docker Bench for Security para auditoria automática:

docker run --net host --pid host --userns host --cap-add audit_control -e DOCKER_CONTENT_TRUST=1 --rm -it aquasec/docker-bench-security



⸻

Resumo das Boas Práticas

✔ Mantenha o Docker e as imagens sempre atualizadas.
✔ Nunca rode containers como root.
✔ Restrinja privilégios e recursos (seccomp, cgroups, AppArmor).
✔ Evite expor o Docker daemon na rede sem TLS.
✔ Use volumes seguros ao invés de bind mounts.
✔ Monitore a atividade dos containers com Falco e Sysdig.

Essas práticas garantem um ambiente mais seguro para rodar containers no Docker. Se quiser aprofundar em alguma parte, me avise! 🚀