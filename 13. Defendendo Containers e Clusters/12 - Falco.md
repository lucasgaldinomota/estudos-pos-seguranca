# Falco

🛡️ Falco – Monitoramento de Segurança para Containers e Kubernetes

O Falco é uma ferramenta de detecção de ameaças em tempo real para containers, Kubernetes e sistemas Linux. Ele usa eBPF para inspecionar chamadas do sistema e identificar atividades suspeitas.

✔ Detecta comportamentos maliciosos em containers 🔍
✔ Baseado em regras personalizáveis 🛠️
✔ Integra-se com Kubernetes, Prometheus e SIEMs 🚀

⸻

1️⃣ Instalando o Falco

📌 Para Linux (Ubuntu/Debian)

curl -fsSL https://falco.org/repo/falcosecurity-packages.asc | sudo tee /etc/apt/trusted.gpg.d/falco.asc
echo "deb https://download.falco.org/packages/deb stable main" | sudo tee /etc/apt/sources.list.d/falcosecurity.list
sudo apt update && sudo apt install falco -y

📌 Para macOS (Homebrew)

brew install falcosecurity/tap/falco

📌 Para Kubernetes (Helm)

helm repo add falcosecurity https://falcosecurity.github.io/charts
helm install falco falcosecurity/falco



⸻

2️⃣ Como Funciona o Falco?

1️⃣ Captura eventos do kernel (usando eBPF) 🔎
2️⃣ Analisa o comportamento baseado em regras 🔥
3️⃣ Gera alertas quando encontra atividades suspeitas 🚨

📌 Exemplo de Regra do Falco (Detectar Shells em Containers)

- rule: Shell Executado no Container
  desc: Detecta a execução de um shell dentro de um container
  condition: container and proc.name in (sh, bash, zsh)
  output: "Alerta! Shell detectado no container (User=%user.name Command=%proc.cmdline)"
  priority: WARNING

Isso dispara um alerta sempre que um shell for aberto dentro de um container!

⸻

3️⃣ Rodando o Falco

sudo falco

📌 Isso iniciará o Falco e começará a monitorar eventos em tempo real.

Para visualizar logs:

sudo journalctl -u falco -f



⸻

4️⃣ Integração com Kubernetes

📌 Para monitorar eventos em um cluster Kubernetes:

kubectl logs -l app=falco -n falco

📌 Para exibir eventos:

kubectl get events --namespace falco



⸻

5️⃣ Falco vs Outras Ferramentas

Ferramenta	Uso Principal	Tecnologia
Falco	Segurança em tempo real	eBPF
Sysdig	Monitoramento e troubleshooting	eBPF
Trivy	Scan de vulnerabilidades	CVE Database

📌 Falco é ideal para detectar ataques em tempo real dentro de containers e Kubernetes! 🚀

⸻

🔐 Conclusão

✔ Falco permite monitoramento de segurança em tempo real 📡
✔ Detecta ataques, execução de shells e anomalias 🔥
✔ Fácil de integrar com Kubernetes, Prometheus e SIEMs 🏗️

Quer um exemplo de uso específico? Me avise! 😊🚀