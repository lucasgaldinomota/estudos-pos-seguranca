# Tipos de Criptografia

Existem dois tipos principais de criptografia, e dentro deles, várias técnicas. Aqui vai um resumo claro e direto:

⸻

🔑 1. Criptografia Simétrica
	•	Uma única chave é usada para criptografar e descriptografar.
	•	Rápida e eficiente, ideal para grandes volumes de dados.
	•	Mas: as duas partes precisam compartilhar a chave de forma segura.

Exemplos:
	•	AES (Advanced Encryption Standard) – muito usado hoje.
	•	DES (Data Encryption Standard) – antigo, mas foi amplamente usado.
	•	RC4, Blowfish, Twofish – outros algoritmos simétricos.

⸻

🔐 2. Criptografia Assimétrica
	•	Usa um par de chaves: uma pública (divulgada) e uma privada (secreta).
	•	Se você criptografa com a chave pública, só a privada pode decifrar — e vice-versa.
	•	Mais segura para troca de chaves, mas mais lenta que a simétrica.

Exemplos:
	•	RSA – um dos mais usados.
	•	ECC (Elliptic Curve Cryptography) – mais leve, ideal para dispositivos móveis.
	•	ElGamal, DSA – também bastante usados.

⸻

📦 Outros tipos complementares:

✅ Criptografia de Hash
	•	Transforma dados em um “resumo” fixo (hash), como SHA-256 ou MD5.
	•	Não é reversível, usada para verificar integridade.
	•	Muito usada em senhas e blockchain.

🔗 Criptografia Híbrida
	•	Combina simétrica + assimétrica:
	•	Usa criptografia assimétrica para trocar a chave,
	•	E simétrica para o restante da comunicação (ex: HTTPS).

⸻

Quer que eu mostre um exemplo simples de criptografia simétrica ou assimétrica em ação?