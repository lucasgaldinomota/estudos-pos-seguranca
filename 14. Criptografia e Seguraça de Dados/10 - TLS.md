# TLS

🔒 O que é TLS?

TLS (Transport Layer Security) é um protocolo de segurança que protege a comunicação entre dois dispositivos — como navegador e servidor — garantindo:
	1.	Confidencialidade (dados criptografados),
	2.	Integridade (sem alterações),
	3.	Autenticidade (você está falando com o site certo).

É o sucessor do SSL (Secure Sockets Layer), que já está obsoleto.

📌 Quando você vê um site com “https://” e o cadeado no navegador, está usando TLS.

⸻

🧰 Como o TLS funciona? (resumo simplificado)

1. Handshake (negociação inicial)
	•	O navegador e o servidor:
	•	Trocam certificados digitais (com chave pública),
	•	Escolhem um algoritmo de criptografia (ex: AES, ChaCha20),
	•	Geram uma chave de sessão compartilhada.

2. Criptografia de dados
	•	Depois do handshake, todos os dados enviados entre cliente e servidor são criptografados com criptografia simétrica (rápida e segura).

3. Verificação de integridade
	•	Usa MAC (Message Authentication Code) ou AEAD (como GCM) para garantir que os dados não foram alterados.

⸻

🔐 Tecnologias usadas no TLS:
	•	Criptografia assimétrica (RSA, ECC) — no início (para troca de chave).
	•	Criptografia simétrica (AES, ChaCha20) — durante a comunicação.
	•	Funções hash (SHA-256, SHA-384) — para integridade.
	•	Certificados digitais (X.509) — para autenticação.

⸻

🧪 Versões do TLS (importante!)
	•	✅ TLS 1.3 — atual, rápido e seguro (lançado em 2018).
	•	⚠️ TLS 1.2 — ainda amplamente usado.
	•	❌ TLS 1.0 e 1.1 — obsoletos e inseguros (não devem mais ser usados).

⸻

🌐 Onde o TLS é usado?
	•	HTTPS (sites seguros)
	•	E-mail (SMTP com STARTTLS)
	•	VPNs (como OpenVPN)
	•	Mensageiros e apps (WhatsApp, Signal, etc.)

⸻

🛡️ Resumo prático:

TLS = canal seguro e confiável entre duas máquinas, protegendo seus dados contra espionagem, fraudes e adulterações.
