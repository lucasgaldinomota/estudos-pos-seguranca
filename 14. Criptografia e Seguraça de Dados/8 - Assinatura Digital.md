# Assinatura Digital

✍️ O que é uma Assinatura Digital?

Uma assinatura digital é um mecanismo criptográfico que garante que uma mensagem ou arquivo:
	1.	É autêntico — foi realmente enviado por quem diz ter enviado.
	2.	Não foi alterado — mantém a integridade dos dados.
	3.	Não pode ser negado — o autor não pode negar que assinou (não-repúdio).

⸻

🧰 Como funciona (resumo técnico):

Ela usa criptografia assimétrica (como RSA ou ECDSA).

Passos principais:
	1.	📩 Criação da assinatura:
	•	O remetente calcula um hash da mensagem (ex: SHA-256).
	•	Usa sua chave privada para criptografar esse hash.
	•	Esse resultado é a assinatura digital, que é enviada junto com a mensagem.
	2.	🔍 Verificação da assinatura:
	•	O destinatário calcula o hash da mensagem recebida.
	•	Descriptografa a assinatura com a chave pública do remetente.
	•	Compara os dois hashes:
	•	Se forem iguais, a mensagem é autêntica e íntegra.
	•	Se forem diferentes, houve alteração ou fraude.

⸻

🔐 Exemplo prático (com RSA):
	•	Alice quer assinar a mensagem “Oi Bob”.
	•	Ela gera o hash (ex: SHA-256 → abc123...)
	•	Criptografa o hash com sua chave privada RSA → assinatura digital.
	•	Envia: "Oi Bob" + assinatura.

Bob:
	•	Gera o hash de “Oi Bob”.
	•	Descriptografa a assinatura com a chave pública da Alice.
	•	Compara os hashes → se batem, a mensagem é legítima.

⸻

✅ Onde é usada:
	•	Assinaturas eletrônicas (PDFs, contratos, e-mails seguros)
	•	Transações de blockchain e criptomoedas (como no Bitcoin e Ethereum)
	•	Softwares (para garantir que o app veio de um desenvolvedor confiável)
	•	Certificados SSL/TLS (garantem que o site é verdadeiro)
