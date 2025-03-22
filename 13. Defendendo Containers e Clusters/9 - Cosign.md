# Cosign

🔐 Cosign – Assinatura e Verificação de Contêineres

📌 O que é o Cosign?

O Cosign é uma ferramenta do Sigstore que permite assinar, verificar e armazenar assinaturas de imagens de contêiner sem modificar a imagem original.

✔ Protege contra ataques de supply chain 🚨
✔ Assinaturas ficam armazenadas no repositório da imagem 📦
✔ Compatível com qualquer registry Docker (Docker Hub, GCR, ECR, etc.)

⸻

1️⃣ Como Funciona a Assinatura com Cosign?
	1.	🔑 Geramos um par de chaves (pública e privada).
	2.	📦 Assinamos a imagem com a chave privada.
	3.	✅ Publicamos a assinatura no mesmo repositório da imagem.
	4.	🔍 Verificamos a assinatura antes de usar a imagem.

Se alguém modificar a imagem, a verificação falha! 🚨

⸻

2️⃣ Instalando o Cosign

📥 Linux/macOS

curl -LO https://github.com/sigstore/cosign/releases/latest/download/cosign-linux-amd64
chmod +x cosign-linux-amd64
sudo mv cosign-linux-amd64 /usr/local/bin/cosign

📥 Windows (PowerShell)

Invoke-WebRequest -Uri "https://github.com/sigstore/cosign/releases/latest/download/cosign-windows-amd64.exe" -OutFile cosign.exe



⸻

3️⃣ Assinando uma Imagem Docker

🔑 Gerar um Par de Chaves

cosign generate-key-pair

Isso cria:
	•	cosign.key → Chave privada (NÃO compartilhe!)
	•	cosign.pub → Chave pública (usada para verificação)

⸻

📦 Assinar a Imagem

cosign sign --key cosign.key meu-registro.com/meu-container:latest

✔ Isso NÃO modifica a imagem!
✔ A assinatura é armazenada no mesmo repositório da imagem.

⸻

4️⃣ Verificando a Assinatura

cosign verify --key cosign.pub meu-registro.com/meu-container:latest

Se a imagem for autêntica, você verá algo como:

Verified OK

Se alguém modificar a imagem, a verificação falha! 🚨

⸻

5️⃣ Usando Cosign sem Chaves (Keyless Signing)

O Cosign suporta autenticação keyless via OIDC (Google, GitHub, etc.).
📌 Isso elimina a necessidade de armazenar chaves privadas!

🔐 Assinar uma Imagem sem Chave

cosign sign meu-registro.com/meu-container:latest

✔ O Cosign usará sua conta do GitHub/GitLab/GCP/AWS para autenticação.

✅ Verificar uma Imagem Keyless

cosign verify meu-registro.com/meu-container:latest



⸻

6️⃣ Integração do Cosign na CI/CD

📌 Exemplo no GitHub Actions:

jobs:
  sign-and-verify:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout código
        uses: actions/checkout@v3

      - name: Instalar Cosign
        run: |
          curl -LO https://github.com/sigstore/cosign/releases/latest/download/cosign-linux-amd64
          chmod +x cosign-linux-amd64
          sudo mv cosign-linux-amd64 /usr/local/bin/cosign

      - name: Construir e Push da Imagem
        run: |
          docker build -t meu-registro.com/meu-container:latest .
          docker push meu-registro.com/meu-container:latest

      - name: Assinar a Imagem
        run: cosign sign --key cosign.key meu-registro.com/meu-container:latest

      - name: Verificar Assinatura
        run: cosign verify --key cosign.pub meu-registro.com/meu-container:latest

📌 Se a verificação falhar, o pipeline CI/CD falha automaticamente! 🚨

⸻

7️⃣ Comparação: Cosign vs Docker Content Trust (DCT)

🔧 Ferramenta	🔍 O que faz?	🚀 Vantagens
Cosign	Assina e verifica imagens sem modificar a imagem	✅ Funciona em qualquer registry, suporta keyless
DCT (Docker Content Trust)	Usa Notary para garantir integridade	❌ Limitado a Docker Hub e Notary-enabled registries

📌 Cosign é mais moderno e flexível, sendo recomendado para novas implementações.

⸻

🔐 Conclusão

✔ Cosign permite assinar e verificar imagens de forma simples e segura.
✔ Funciona com qualquer repositório Docker (Docker Hub, GCR, ECR, etc.).
✔ Suporta autenticação sem chave (Keyless Signing).
✔ Deve ser integrado na CI/CD para garantir a segurança dos contêineres.

Se precisar de mais detalhes ou ajuda para configurar, me avise! 🚀