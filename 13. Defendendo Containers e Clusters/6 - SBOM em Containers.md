# SBOM em Containers

SBOM em Containers 🛡️🚢

O que é SBOM?

O SBOM (Software Bill of Materials) é um inventário detalhado de todos os componentes de software em uma aplicação ou container. Ele ajuda a:
✔ Identificar vulnerabilidades em dependências de terceiros.
✔ Garantir conformidade com requisitos de segurança e auditoria.
✔ Rastrear pacotes usados em cada versão do container.

⸻

1️⃣ Por que SBOM é Importante em Containers?

Containers são compostos por:
	•	Um sistema operacional base (Ubuntu, Alpine, Distroless, etc.).
	•	Linguagens e bibliotecas (Node.js, Python, Java, etc.).
	•	Aplicação final desenvolvida pelo time.

Se um componente tiver uma vulnerabilidade, pode afetar toda a aplicação!
O SBOM permite saber exatamente quais pacotes e versões estão no container para identificar riscos rapidamente.

⸻

2️⃣ Como Gerar um SBOM para Containers?

Existem várias ferramentas para gerar um SBOM de um container:

📌 Syft (Anchore)

📥 Instale o Syft:

curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sudo sh -s -- -b /usr/local/bin

📦 Gerar um SBOM para um container rodando:

syft docker:meu-container

📦 Gerar um SBOM para uma imagem local:

syft meu-container:latest -o table

📦 Gerar um SBOM em formato JSON ou SPDX:

syft meu-container:latest -o json > sbom.json



⸻

📌 Trivy (Aqua Security)

O Trivy faz análise de vulnerabilidades e pode gerar um SBOM.
📥 Instale o Trivy:

sudo apt install wget -y
wget https://github.com/aquasecurity/trivy/releases/latest/download/trivy_Linux_amd64.tar.gz
tar -xvf trivy_Linux_amd64.tar.gz
sudo mv trivy /usr/local/bin/

📦 Gerar um SBOM:

trivy sbom --format json -o sbom.json meu-container:latest

📦 Verificar vulnerabilidades baseadas no SBOM:

trivy image meu-container:latest



⸻

📌 Docker Scout (Oficial da Docker)

📦 Gerar um SBOM diretamente com Docker:

docker scout sbom meu-container:latest



⸻

3️⃣ Formatos de SBOM

SBOMs podem ser gerados em diferentes formatos:

Formato	Descrição
SPDX	Padrão usado pela Linux Foundation.
CycloneDX	Criado pela OWASP para segurança.
JSON / YAML	Formatos genéricos e legíveis por máquinas.

📌 Exemplo de SBOM em JSON:

{
  "name": "meu-container",
  "version": "latest",
  "components": [
    {
      "name": "openssl",
      "version": "1.1.1k",
      "type": "library"
    },
    {
      "name": "nginx",
      "version": "1.21.3",
      "type": "application"
    }
  ]
}



⸻

4️⃣ Integrando SBOM na Pipeline CI/CD

📌 Exemplo usando Syft em um pipeline GitHub Actions:

jobs:
  generate-sbom:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout código
        uses: actions/checkout@v3

      - name: Instalar Syft
        run: |
          curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b /usr/local/bin

      - name: Construir e gerar SBOM
        run: |
          docker build -t meu-container:latest .
          syft docker:meu-container:latest -o json > sbom.json

      - name: Upload SBOM
        uses: actions/upload-artifact@v3
        with:
          name: sbom
          path: sbom.json

🚀 Isso gera um SBOM automaticamente em cada build!

⸻

5️⃣ Como Usar o SBOM para Segurança?
	•	Verificar pacotes vulneráveis com Trivy:

trivy image --sbom sbom.json meu-container:latest


	•	Rastrear mudanças em dependências ao longo do tempo.
	•	Garantir conformidade com padrões como NIST, ISO e OWASP.
	•	Auditar terceiros e fornecedores que entregam software em containers.

⸻

🔐 Conclusão

✔ SBOMs são essenciais para rastrear o que está em um container.
✔ Ferramentas como Syft, Trivy e Docker Scout facilitam a geração.
✔ Integre SBOM na CI/CD para verificar vulnerabilidades automaticamente.
✔ Ajuda na conformidade com padrões de segurança e auditoria.

Quer mais detalhes sobre SBOMs ou integração com outras ferramentas? 🚀