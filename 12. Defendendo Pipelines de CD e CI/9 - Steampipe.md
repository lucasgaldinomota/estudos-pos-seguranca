# Steampipe

🧩 Steampipe

O Steampipe é uma plataforma de código aberto que permite consultar APIs, serviços em nuvem e bancos de dados usando SQL. Ele converte APIs em tabelas SQL, facilitando a análise, monitoramento e auditoria de sistemas complexos sem a necessidade de escrever código adicional.

🔗 Site Oficial | 🗃️ Repositório no GitHub

🚀 1. Vantagens do Steampipe

✅ Consultas SQL em APIs: Use SQL padrão para consultar APIs como AWS, GitHub, GitLab, OpenSSF Scorecard, entre outras.
✅ Auditorias de Segurança: Monitore conformidade com PCI-DSS, CIS Benchmarks, NIST, SOC 2, etc.
✅ Plugins Flexíveis: Plugins para diversos provedores como AWS, GCP, Azure, GitHub, Kubernetes e Docker.
✅ Dashboards Interativos: Crie dashboards em tempo real usando o Steampipe Dashboard.
✅ Automação no CI/CD: Integre o Steampipe em pipelines de CI/CD para auditoria contínua.

💾 2. Instalação

Linux/Mac:

curl -sSL https://steampipe.io/install | sudo bash

Windows:

Baixe o instalador no site oficial.

📦 3. Plugins do Steampipe

Após instalar, adicione plugins com o comando:

steampipe plugin install github
steampipe plugin install aws
steampipe plugin install scorecard

🗂️ 4. Exemplos de Consultas

🔍 4.1 Consultando Repositórios GitHub

Arquivo de configuração: ~/.steampipe/config/github.spc

connection "github" {
  plugin = "github"
  token  = "ghp_seu_token_aqui" # Token do GitHub para acesso autenticado
}

Consulta SQL para listar repositórios de uma organização:

select name, owner_login, stargazers_count
from github_repository
where owner_login = 'openai';

🛡️ 4.2 Análise de Segurança com OpenSSF Scorecard

Arquivo de configuração: ~/.steampipe/config/scorecard.spc

connection "scorecard" {
  plugin = "scorecard"
}

Consulta SQL para obter a pontuação de um repositório:

select repo, score, checks
from scorecard_repository
where repo = 'github.com/ossf/scorecard';

Resultado:

repo                                score  checks
---------------------------------  -----  ----------------------------------------------------
github.com/ossf/scorecard           9.2   {"Code-Review":"PASS", "Branch-Protection":"PASS"}

🌐 4.3 Consultando AWS para Auditoria PCI-DSS

select account_id, region, title, status
from aws_compliance_control
where standard_name = 'PCI-DSS' and status = 'FAIL';

📊 5. Dashboards com Steampipe

Crie dashboards usando o Steampipe Dashboard:

steampipe dashboard serve

Abra o navegador em http://localhost:9194.

Exemplo de painel para GitHub:

dashboard "github_overview" {
  title = "GitHub Overview"
  section "Repositories" {
    widget {
      title = "Top Repositories by Stars"
      query = <<EOT
        select name, stargazers_count
        from github_repository
        order by stargazers_count desc
        limit 5;
      EOT
    }
  }
}

🔗 6. Integração com CI/CD

Automatize auditorias de segurança no seu pipeline de CI/CD usando Steampipe em GitHub Actions:

name: Security Audit with Steampipe

on:
  push:
    branches: [main]
  workflow_dispatch:

jobs:
  audit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Install Steampipe
        run: curl -sSL https://steampipe.io/install | sudo bash

      - name: Install Plugins
        run: steampipe plugin install scorecard github

      - name: Run OpenSSF Scorecard Check
        run: steampipe query "select repo, score from scorecard_repository where repo = 'github.com/org/repo';"

💡 7. Casos de Uso em CI/CD

✅ Auditoria de Conformidade: Garanta que o pipeline CI/CD esteja em conformidade com PCI-DSS, CIS, NIST, etc.
✅ Segurança de Repositórios SCM: Monitore o OpenSSF Scorecard automaticamente.
✅ Automatização de Relatórios: Gere relatórios de segurança após cada build.
✅ Monitoramento de Cloud: Verifique configurações de segurança em AWS, GCP e Azure.

🌱 Conclusão

O Steampipe é uma ferramenta poderosa para monitorar e auditar segurança em ambientes de CI/CD, repositórios de código e serviços em nuvem. Sua capacidade de usar SQL para consultar APIs facilita a integração com pipelines de CI/CD, tornando-o essencial para garantir conformidade e segurança contínuas. 🚀🛡️

Se quiser, posso criar o script de configuração do Steampipe para o seu projeto ou integrar ao backend em Express.js. 😊