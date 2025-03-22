# Assinatura de Containers

🛡️ Assinatura de Contêineres – Garantindo a Integridade

A assinatura de contêineres permite verificar a autenticidade e integridade das imagens antes do uso. Isso protege contra:
✔ Alterações não autorizadas na imagem 📦
✔ Ataques de supply chain 🕵️‍♂️
✔ Uso de imagens comprometidas 🚨

⸻

1️⃣ Como Funciona a Assinatura de Contêineres?
	1.	Geramos uma assinatura digital da imagem Docker usando uma chave privada.
	2.	Publicamos a assinatura junto com a imagem no repositório.
	3.	Os usuários verificam a assinatura antes de puxar a imagem.

Isso garante que a imagem foi realmente criada por quem afirma ser o autor e que não foi alterada.

⸻

2️⃣ Ferramentas para Assinar Contêineres

🔧 Ferramenta	🔍 Função
Cosign	Assina e verifica imagens sem modificar a própria imagem
Docker Content Trust (DCT)	Usa Notary para garantir integridade
Sigstore	Framework moderno para assinaturas automáticas



⸻

3️⃣ Assinando Imagens com Cosign (Sigstore)

📌 Cosign é a ferramenta mais moderna para assinatura de contêineres e faz parte do Sigstore.

📥 Instalando o Cosign

curl -LO https://github.com/sigstore/cosign/releases/latest/download/cosign-linux-amd64
chmod +x cosign-linux-amd64
sudo mv cosign-linux-amd64 /usr/local/bin/cosign



⸻

📝 Gerar uma Chave para Assinar

cosign generate-key-pair

Isso cria dois arquivos:
	•	cosign.key (chave privada) 🔑
	•	cosign.pub (chave pública) 🔓

⸻

📌 Assinando uma Imagem Docker

cosign sign --key cosign.key meu-container:latest

📌 Isso não modifica a imagem! A assinatura fica armazenada no repositório da imagem.

⸻

✅ Verificando a Assinatura

cosign verify --key cosign.pub meu-container:latest

Se a assinatura for válida, você verá algo como:

Verified OK

Se alguém modificar a imagem, a verificação falhará. 🚨

⸻

4️⃣ Usando Docker Content Trust (DCT)

O Docker Content Trust (DCT) usa Notary para validar imagens.

🔹 Habilitar DCT no Docker

export DOCKER_CONTENT_TRUST=1

🔹 Assinar uma Imagem

docker trust sign meu-registro.com/meu-container:latest

🔹 Verificar a Assinatura

docker trust inspect --pretty meu-registro.com/meu-container:latest

📌 DCT só funciona com repositórios que suportam Notary, como Docker Hub e Harbor.

⸻

5️⃣ Integração da Assinatura na CI/CD

📌 Exemplo no GitHub Actions usando Cosign:

jobs:
  sign-and-push:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout código
        uses: actions/checkout@v3

      - name: Construir Imagem Docker
        run: docker build -t meu-container:latest .

      - name: Login no Registro
        run: echo "${{ secrets.DOCKER_PASSWORD }}" | docker login -u "${{ secrets.DOCKER_USERNAME }}" --password-stdin

      - name: Push da Imagem
        run: docker push meu-container:latest

      - name: Assinar Imagem com Cosign
        run: cosign sign --key cosign.key meu-container:latest

📌 Isso garante que apenas imagens assinadas sejam publicadas.

⸻

6️⃣ Conclusão

✔ Assinar imagens Docker evita ataques de supply chain.
✔ Cosign é a ferramenta mais moderna para assinaturas.
✔ Docker Content Trust é útil, mas tem suporte limitado.
✔ Verificar assinaturas antes do deploy melhora a segurança.

Quer mais detalhes sobre Cosign ou DCT? Me avise! 🚀