# Certificado Digital

📄 O que é um Certificado Digital?

Um certificado digital é como uma carteira de identidade digital que comprova que uma chave pública pertence a uma pessoa, empresa ou site específico.

Ele é emitido por uma autoridade certificadora (CA) confiável, como o Serasa, Certisign, Let’s Encrypt, entre outras.

⸻

🔐 O que ele contém?

Um certificado digital inclui:
	•	Nome do titular (pessoa, empresa ou site)
	•	Chave pública
	•	Assinatura digital da autoridade certificadora
	•	Validade
	•	Número de série
	•	Algoritmo usado (ex: RSA, SHA-256)
	•	Autoridade emissora (CA)

⸻

🧭 Para que serve?
	1.	Autenticação
→ Prova que você é você (ex: login em sistemas do governo ou bancos).
	2.	Assinatura digital de documentos
→ Dá validade jurídica (ex: contratos, notas fiscais eletrônicas).
	3.	Segurança em sites (HTTPS)
→ Os navegadores verificam o certificado para saber se o site é legítimo.

⸻

🧰 Tipos comuns de certificados digitais:

📌 Pessoais (e-CPF / e-CNPJ)
	•	Usado por pessoas físicas ou empresas para assinar documentos e acessar serviços do governo (Receita Federal, eSocial, etc).

🌐 Certificados SSL/TLS (para sites)
	•	Garante que a conexão entre o navegador e o site é segura (ex: 🔒 na barra do navegador).

⸻

🧠 Como funciona por trás dos panos?
	1.	Um site (ou pessoa) gera um par de chaves (pública e privada).
	2.	Envia a chave pública para uma CA.
	3.	A CA verifica e emite o certificado digital, assinando digitalmente a chave pública.
	4.	Quando alguém acessa o site ou documento, pode:
	•	Verificar a assinatura digital da CA,
	•	Confiar que a chave pública realmente pertence àquela entidade.
