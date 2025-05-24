# DVWA

🔍 O que é o DVWA?

DVWA é um ambiente de treino que simula um sistema vulnerável, onde você pode praticar ataques web de forma legal e controlada.

⸻

🚀 Como rodar o DVWA com Docker (recomendado)

A forma mais fácil é usar Docker:

🔧 1. Instalar Docker (se ainda não tiver)

Linux:

sudo apt install docker.io -y

Windows/Mac: usar Docker Desktop

📦 2. Rodar DVWA via Docker

docker run --rm -it -p 80:80 vulnerables/web-dvwa

Isso vai rodar o DVWA e expor ele em http://localhost ou http://<seu_ip> na porta 80.

⸻

🛠 Primeira configuração
	1.	Acesse http://localhost
	2.	Usuário padrão:
	•	Username: admin
	•	Password: password
	3.	Clique em Create / Reset Database
	4.	DVWA está pronto para uso

⸻

🎯 O que você pode praticar no DVWA

DVWA tem níveis de segurança: low, medium, high e impossible.

Ataques disponíveis:
	•	SQL Injection
	•	Blind SQL Injection
	•	Command Execution
	•	XSS (Reflected e Stored)
	•	CSRF
	•	File Upload
	•	Brute Force
	•	Insecure CAPTCHA
	•	User Agent Injection

⸻

🔐 Dicas de segurança para estudo
	•	Rode o DVWA em uma VM isolada ou rede NAT/local
	•	Nunca exponha o container para a internet
	•	Use ferramentas como:
	•	Burp Suite (proxy/interceptador)
	•	sqlmap (para SQLi automatizada)
	•	curl, wfuzz, dirb, etc.

⸻

📁 Se quiser montar DVWA sem Docker (manual):

Requer:
	•	Apache/Nginx
	•	PHP
	•	MySQL
	•	git clone do repositório:

git clone https://github.com/digininja/DVWA.git