# OpenSSF Scorecard

OpenSSF Scorecard

O OpenSSF Scorecard é uma ferramenta automatizada que avalia a segurança de projetos de código aberto. Ele pertence à Open Source Security Foundation (OpenSSF), que faz parte da Linux Foundation, e tem como objetivo ajudar desenvolvedores e empresas a identificarem riscos em dependências de código aberto.

1. Como Funciona o OpenSSF Scorecard?

O Scorecard realiza análises automatizadas em repositórios de código aberto, atribuindo uma pontuação de 0 a 10 com base em diversos critérios de segurança.

Principais verificações feitas pelo Scorecard:

✅ GitHub Actions Security – Avalia a segurança dos fluxos de CI/CD no GitHub.
✅ Branch Protection – Verifica se o projeto tem regras de proteção de branches.
✅ Code Review – Confere se as mudanças no código passam por revisões antes de serem aceitas.
✅ Signed Releases – Avalia se o projeto usa assinaturas digitais para liberar versões seguras.
✅ Dependency Update Tool – Verifica se há uso de ferramentas como Dependabot para manter dependências atualizadas.
✅ Binary Artifacts – Identifica binários não rastreáveis dentro do repositório.
✅ Pinned Dependencies – Avalia se o projeto fixa versões de dependências para evitar supply chain attacks.
✅ Security Policy – Confirma se o projeto possui uma política de segurança pública (SECURITY.md).
✅ Maintained – Mede a frequência de commits e atividade da comunidade para avaliar se o projeto está ativo.

2. Como Usar o OpenSSF Scorecard?

1️⃣ Executando via GitHub Actions

Se o seu repositório está no GitHub, você pode integrar o Scorecard ao seu pipeline de CI/CD adicionando este workflow:

name: OpenSSF Scorecard

on:
  schedule:
    - cron: '0 12 * * 1' # Executa toda segunda-feira ao meio-dia
  workflow_dispatch: # Permite execução manual

jobs:
  scorecard:
    runs-on: ubuntu-latest
    steps:
      - name: Run OpenSSF Scorecard
        uses: ossf/scorecard-action@v2
        with:
          results_file: results.json

2️⃣ Executando Localmente

Você também pode rodar o Scorecard manualmente no terminal:
	1.	Instale o Scorecard:

go install github.com/ossf/scorecard/v4@latest


	2.	Execute a análise em um repositório:

scorecard --repo=https://github.com/nome-do-repositorio

3. Benefícios do OpenSSF Scorecard

🔹 Identifica riscos automaticamente – Detecta práticas inseguras em repositórios de código aberto.
🔹 Ajuda na conformidade – Auxilia a manter padrões de segurança exigidos por normas como PCI DSS, NIST, ISO 27001.
🔹 Evita ataques à supply chain – Reduz riscos associados a dependências comprometidas.
🔹 Facilidade de integração – Funciona nativamente com GitHub Actions e outras ferramentas CI/CD.