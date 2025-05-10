# Colisão

💥 O que é uma colisão em criptografia?

Uma colisão ocorre quando duas entradas diferentes produzem a mesma saída em uma função hash.

Exemplo ilustrativo:

hash("Mensagem A") = 5F4DCC3B5AA765D61D8327DEB882CF99  
hash("Mensagem B") = 5F4DCC3B5AA765D61D8327DEB882CF99  ← Colisão!

Mesmo que “Mensagem A” ≠ “Mensagem B”, elas geraram o mesmo hash. Isso não deveria acontecer, mas pode acontecer com funções hash mal projetadas ou que já foram superadas por avanços tecnológicos.

⸻

🧠 Por que colisões são um problema?
	•	Funções hash são usadas para garantir a integridade dos dados.
	•	Em sistemas de segurança (como assinaturas digitais), se for possível forjar uma segunda mensagem com o mesmo hash, a confiança é quebrada.
	•	Isso pode levar a fraudes, falsificações ou execução de código malicioso.

⸻

🧨 Exemplos reais de colisões:
	•	MD5: Vulnerável desde os anos 2000. Em 2008, pesquisadores criaram certificados digitais falsos com colisões de MD5.
	•	SHA-1: Teve sua primeira colisão comprovada em 2017 (projeto SHAttered do Google e CWI Amsterdam).

⸻

✅ Como evitamos colisões hoje?
	•	Usamos funções hash criptográficas modernas, como:
	•	SHA-256
	•	SHA-3
	•	BLAKE3
	•	Evitamos funções hash obsoletas (como MD5 e SHA-1).
