# Vms vs Containers

⚔️ VMs vs Containers: Comparativo Rápido

Característica	Máquina Virtual (VM)	Container
Isolamento	Forte (via hypervisor, simula hardware completo)	Médio (compartilha o kernel do host)
Sistema Operacional	Cada VM roda seu próprio SO	Todos compartilham o mesmo SO do host
Desempenho	Mais pesado (boot lento, uso de recursos maior)	Leve e rápido (inicia em milissegundos)
Segurança	Maior isolamento, difícil escapar da VM	Menor isolamento, containers podem escapar se mal configurados
Tamanho da imagem	GBs (contém SO completo)	MBs (só app + dependências)
Gerenciamento	Mais complexo (hypervisor, snapshots, etc.)	Mais simples (Docker CLI, Kubernetes)
Exemplo de uso	Infra tradicional, apps legados, segurança forte	Microserviços, DevOps, CI/CD


⸻

🔐 Segurança: Qual é mais seguro?

✅ VMs: Mais seguras por padrão
	•	Isolamento a nível de hardware com hypervisor (ex: VMware, KVM, Hyper-V)
	•	Ataques como “VM Escape” são raros e difíceis (ex: CVE-2017-5715 - Spectre)

⚠️ Containers: Mais vulneráveis se mal configurados
	•	Compartilham kernel do host → ataque de escape é mais viável
	•	Exemplos:
	•	CVE-2019-5736: escape do Docker via runC
	•	Montar /var/run/docker.sock → acesso root ao host
	•	Containers privilegiados podem ler o sistema de arquivos do host

⸻

🛠 Em Labs e Pentest…
	•	Use VMs para simular o host seguro (ex: Kali, Ubuntu com Docker)
	•	Use containers como alvo (mais vulneráveis, mais rápidos de reiniciar)
	•	Você pode rodar containers dentro de VMs para praticar ataques de escape com segurança

⸻

🔍 Exemplo prático:

Container Attack:

docker run -v /:/host --rm -it alpine chroot /host

➡️ Isso dá acesso total ao host se o container estiver mal configurado (privileged ou volume root).

VM Escape:
Muito mais complexo. Exige falha de hypervisor, acesso root, e uma vulnerabilidade específica.