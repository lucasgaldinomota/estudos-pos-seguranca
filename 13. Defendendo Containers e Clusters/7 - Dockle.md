# Dockle

Dockle – Auditoria de Segurança em Containers 🔍🛡️

📌 O que é o Dockle?

O Dockle é uma ferramenta de análise de segurança para imagens Docker, focada em boas práticas e configuração segura. Ele não verifica vulnerabilidades de pacotes (como o Trivy), mas alerta sobre:

✔ Uso de imagens como root 🚨
✔ Permissões inseguras em arquivos 🔐
✔ Uso de pacotes desatualizados 📦
✔ Exposição de credenciais 🔑
✔ Configurações inseguras do Dockerfile 📜

⸻

1️⃣ Como Instalar o Dockle?

📥 Instalação no Linux/macOS

curl -LO https://github.com/goodwithtech/dockle/releases/latest/download/dockle_Linux_x86_64
chmod +x dockle_Linux_x86_64
sudo mv dockle_Linux_x86_64 /usr/local/bin/dockle

📌 Para macOS (usando Homebrew):

brew install goodwithtech/r/dockle

📥 Instalação no Windows
	1.	Baixe o binário AQUI
	2.	Adicione-o ao PATH do sistema.

⸻

2️⃣ Como Usar o Dockle?

🔍 Verificando uma Imagem Docker

dockle meu-container:latest

📌 Isso analisa a imagem e exibe problemas de segurança.

⸻

3️⃣ Exemplo de Saída do Dockle

WARN  - CIS-DI-0001: Create a user for the container
WARN  - CIS-DI-0005: Enable Content trust for Docker
WARN  - CIS-DI-0006: Add HEALTHCHECK instruction to the container image
INFO  - DKL-DI-0007: Set specific user (not root) in Dockerfile

🔴 CRITICAL → Problemas graves ⚠️
🟠 WARN → Problemas importantes 💡
🔵 INFO → Boas práticas

⸻

4️⃣ Configurações Comuns do Dockle

🔎 Ignorar uma Regra Específica

dockle --ignore CIS-DI-0001 meu-container:latest

📜 Gerar Relatório em JSON

dockle -f json -o report.json meu-container:latest

🚀 Definir um Nível Mínimo de Segurança

dockle --exit-code 1 meu-container:latest

📌 Isso faz com que o comando falhe se encontrar problemas de segurança.

⸻

5️⃣ Integração do Dockle na CI/CD

📌 GitHub Actions

jobs:
  security-audit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout código
        uses: actions/checkout@v3

      - name: Instalar Dockle
        run: |
          curl -LO https://github.com/goodwithtech/dockle/releases/latest/download/dockle_Linux_x86_64
          chmod +x dockle_Linux_x86_64
          sudo mv dockle_Linux_x86_64 /usr/local/bin/dockle

      - name: Construir Imagem Docker
        run: docker build -t meu-container:latest .

      - name: Analisar Segurança com Dockle
        run: dockle --exit-code 1 meu-container:latest

🔐 Se o Dockle encontrar falhas críticas, o pipeline falha automaticamente.

⸻

6️⃣ Comparação: Dockle vs Trivy vs Syft

Ferramenta	Foco	O que verifica?
Dockle	Configuração Segura	Usuário root, permissões, Dockerfile
Trivy	Vulnerabilidades	CVEs em pacotes e SO
Syft	SBOM	Lista todos os pacotes

📌 Dockle + Trivy é uma combinação ideal para segurança completa de containers.

⸻

🔐 Conclusão

✔ Dockle ajuda a evitar configurações inseguras no Docker.
✔ Fácil de usar e integrar em pipelines CI/CD.
✔ Complementa o Trivy (para CVEs) e o Syft (para SBOM).
✔ Melhor prática para DevSecOps! 🚀

Quer mais detalhes ou um exemplo para sua aplicação? Me avise! 😊