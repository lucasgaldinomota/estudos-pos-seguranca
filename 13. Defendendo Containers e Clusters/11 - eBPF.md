# eBPF

🛡️ eBPF – Observabilidade e Segurança no Kernel do Linux

O eBPF (Extended Berkeley Packet Filter) é uma tecnologia que permite executar código no kernel do Linux sem precisar modificá-lo ou reiniciá-lo.

✔ Alta performance 🚀
✔ Monitoramento e segurança em tempo real 🛡️
✔ Ideal para Kubernetes e containers 🏗️

⸻

1️⃣ O que é eBPF?

O eBPF permite rodar programas dentro do kernel de forma segura e eficiente, sendo usado para:

✔ Observabilidade (monitoramento de rede, syscalls, latência) 👀
✔ Segurança (firewalls, prevenção de ataques) 🔥
✔ Otimização de desempenho (tracing, análise de I/O) 🚀

📌 Empresas como Meta, Google, Netflix e Cloudflare usam eBPF para otimizar e proteger seus sistemas.

⸻

2️⃣ Como Funciona o eBPF?

1️⃣ O programa eBPF é escrito em C ou Rust 📝
2️⃣ Ele é compilado em bytecode eBPF ⚙️
3️⃣ O kernel do Linux valida e executa o bytecode 🔍
4️⃣ O programa coleta dados ou modifica o comportamento do sistema 📡

📌 Isso acontece sem precisar modificar o código do kernel!

⸻

3️⃣ Ferramentas Baseadas em eBPF

🛠️ Ferramenta	📌 Uso
BCC	Observabilidade (tracing, métricas)
bpftrace	Debugging avançado com scripts simples
Cilium	Segurança e rede para Kubernetes
Falco	Monitoramento de segurança em containers
Pixie	Observabilidade automática para Kubernetes



⸻

4️⃣ Exemplo: Monitorando Syscalls com eBPF

📌 Instalar o bpftrace:

sudo apt install bpftrace -y

📌 Rodar um script eBPF para monitorar chamadas ao open():

sudo bpftrace -e 'tracepoint:syscalls:sys_enter_open { printf("%s opened %s\n", comm, str(args->filename)); }'

Isso mostra quais processos estão abrindo arquivos em tempo real! 🔍

⸻

5️⃣ eBPF no Kubernetes (Cilium)

📌 O Cilium usa eBPF para:
✔ Segurança de rede (firewall e policies) 🔥
✔ Observabilidade de tráfego 🔍
✔ DNS-aware networking 🌍

🔹 Instalar Cilium no Kubernetes

helm repo add cilium https://helm.cilium.io/
helm install cilium cilium/cilium --namespace kube-system

🔹 Verificar o Status

kubectl get pods -n kube-system | grep cilium

📌 Agora o cluster Kubernetes tem segurança e observabilidade avançada com eBPF! 🚀

⸻

6️⃣ Benefícios do eBPF

✔ Menos overhead que ferramentas tradicionais 🏎️
✔ Execução segura dentro do kernel 🔐
✔ Substitui ferramentas como iptables, tcpdump, strace 🛠️
✔ Perfeito para Kubernetes, containers e cloud ☁️

⸻

🔐 Conclusão

✔ eBPF transforma o kernel do Linux em uma plataforma programável
✔ Ótimo para segurança, monitoramento e performance
✔ Ferramentas como Cilium, Falco e Pixie trazem eBPF para Kubernetes

Quer um exemplo mais prático? Me avise! 🚀