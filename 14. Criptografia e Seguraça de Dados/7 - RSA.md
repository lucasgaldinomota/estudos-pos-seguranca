# RSA

🔐 O que é RSA?

RSA (sigla para Rivest–Shamir–Adleman) é um algoritmo de criptografia assimétrica, criado em 1977. Ele usa um par de chaves:
	•	Chave pública para criptografar
	•	Chave privada para descriptografar

É amplamente usado em:
	•	HTTPS (SSL/TLS),
	•	Assinaturas digitais,
	•	Troca segura de chaves (por exemplo, com AES).

⸻

⚙️ Como funciona o RSA? (resumo simplificado)
	1.	Geração das chaves:
	•	Escolhem-se dois grandes números primos: p e q.
	•	Calcula-se n = p × q (parte da chave pública).
	•	Calcula-se φ(n) = (p − 1) × (q − 1).
	•	Escolhe-se e (expoente público), tal que 1 < e < φ(n) e e seja coprimo com φ(n).
	•	Calcula-se d, o inverso modular de e mod φ(n) → isso é a chave privada.
	2.	Criptografia (feita com a chave pública):
	•	Mensagem (M) → C = M^e mod n
	3.	Descriptografia (feita com a chave privada):
	•	M = C^d mod n

⸻

🧪 Exemplo simplificado (com números pequenos só para ilustrar):
	1.	p = 61, q = 53
	2.	n = 61 × 53 = 3233
	3.	φ(n) = 3120
	4.	Escolhe-se e = 17
	5.	Calcula-se d = 2753
	6.	Mensagem M = 65
	•	Criptografada: C = 65^17 mod 3233 = 2790
	•	Descriptografada: M = 2790^2753 mod 3233 = 65

⸻

🧠 Pontos fortes:
	•	Segurança baseada na dificuldade de fatorar grandes números.
	•	Não exige troca prévia de chave secreta.

⚠️ Pontos fracos:
	•	Lento para grandes volumes de dados → por isso é usado combinado com AES (criptografia híbrida).
	•	Vulnerável se os números primos forem mal escolhidos ou pequenos.
