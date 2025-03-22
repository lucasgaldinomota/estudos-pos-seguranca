# Falco Sidekick

🐦 Falco Sidekick – Integração de Alertas do Falco

O Falco Sidekick é um serviço complementar ao Falco que encaminha alertas de segurança para diferentes destinos, como:

✔ Slack, Discord, Teams 💬
✔ Elasticsearch, Loki, Prometheus 📊
✔ AWS S3, Google Cloud Storage ☁️
✔ SIEMs como Splunk, Datadog, New Relic 🔍

⸻

1️⃣ Instalando o Falco Sidekick

📌 Para Kubernetes (Helm)

helm repo add falcosecurity https://falcosecurity.github.io/charts
helm install falco falcosecurity/falco --set falcosidekick.enabled=true

Isso instala Falco + Falco Sidekick no cluster.

📌 Para Docker

docker run -d -p 2801:2801 falcosecurity/falcosidekick

O Sidekick escuta na porta 2801 e recebe eventos do Falco.

⸻

2️⃣ Configurando o Falco para Usar o Sidekick

Edite o arquivo de configuração do Falco (/etc/falco/falco.yaml):

json_output: true
program_output:
  enabled: true
  keep_alive: false
  output: |
    curl -X POST -H "Content-Type: application/json" -d @- http://localhost:2801

📌 Isso faz com que os alertas do Falco sejam enviados para o Sidekick! 🚀

⸻

3️⃣ Configurando Destinos no Falco Sidekick

Edite o arquivo /etc/falco/falcosidekick.yaml para definir destinos:

slack:
  webhookurl: "https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXXXXXXXXXX"
  icon: ":warning:"
  username: "Falco Alert"

📌 Agora, os alertas do Falco aparecerão no Slack! 🎉

⸻

4️⃣ Verificando Logs do Sidekick

kubectl logs -l app=falco-sidekick -n falco

📌 Isso mostra se os eventos estão sendo encaminhados corretamente.

⸻

5️⃣ Visualizando Alertas no Falco UI

O Falco Sidekick também pode ser integrado ao Falco Sidekick UI, uma interface gráfica para visualizar alertas.

📌 Rodar a UI com Docker

docker run -d -p 2802:2802 falcosecurity/falcosidekick-ui

📌 Acessar no navegador:

http://localhost:2802

Agora você pode visualizar alertas do Falco em tempo real! 🎯

⸻

🔐 Conclusão

✔ Falco Sidekick facilita a integração dos alertas do Falco.
✔ Suporta múltiplos destinos (Slack, SIEMs, Prometheus, etc.).
✔ Fácil de configurar e visualizar eventos com UI própria.

Quer um exemplo para um destino específico? Me avise! 🚀