# Scorecard

OpenSSF Scorecard 🛡️🔍

O OpenSSF Scorecard é uma ferramenta automatizada que avalia a segurança dos projetos de código aberto com base em um conjunto de critérios padronizados. Criado pela Open Source Security Foundation (OpenSSF), o Scorecard ajuda desenvolvedores e empresas a identificar riscos de segurança e boas práticas nos repositórios de software.

✅ 1. Benefícios do OpenSSF Scorecard
	•	Avaliação Rápida: Fornece uma pontuação de segurança baseada em verificações automáticas.
	•	Boas Práticas de Segurança: Analisa a presença de MFA, GitHub Actions seguras, controle de branch, entre outros.
	•	Melhoria Contínua: Ajuda a identificar áreas onde o projeto pode melhorar em segurança.
	•	Transparência: As pontuações são públicas, promovendo confiança na comunidade open-source.

🧩 2. Critérios de Avaliação (Checks)

O Scorecard realiza mais de 20 verificações, incluindo:

Critério	Descrição
Branch-Protection	Verifica se há proteção nas branches principais.
Token-Permissions	Avalia as permissões de tokens em GitHub Actions.
Code-Review	Garante que todo o código passe por revisão antes do merge.
Vulnerabilities	Detecta dependências com vulnerabilidades conhecidas.
CI-Tests	Verifica se há pipelines de testes automatizados.
Pinned-Dependencies	Garante que as dependências estejam com versões fixas.
Dangerous-Workflow	Identifica workflows inseguros que podem ser explorados.
Security-Policy	Checa se há um arquivo SECURITY.md no repositório.
Signed-Releases	Verifica se os releases são assinados digitalmente.
Maintained	Analisa a frequência de commits para avaliar a manutenção.

🛠️ 3. Como Usar o OpenSSF Scorecard

3.1 Executar Localmente

Para executar o Scorecard localmente, instale o CLI via Go:

go install github.com/ossf/scorecard/v4@latest

Depois, execute o comando:

scorecard --repo=https://github.com/org/repo

Exemplo de saída:

RESULTS
-------
Aggregate score: 8.5 / 10
Checks:
- Code-Review: PASS (10/10)
- Branch-Protection: WARN (8/10)
- Token-Permissions: PASS (10/10)
- Dangerous-Workflow: FAIL (3/10)
- Security-Policy: PASS (10/10)

3.2 Integração com GitHub Actions

Você pode configurar o Scorecard no seu pipeline de CI/CD usando GitHub Actions.

Exemplo de workflow:

name: OpenSSF Scorecard
on:
  schedule:
    - cron: '0 6 * * 1'  # Executa semanalmente às 6h de segunda-feira
  workflow_dispatch:  # Permite execução manual

jobs:
  scorecard:
    runs-on: ubuntu-latest
    steps:
      - name: Run Scorecard
        uses: ossf/scorecard-action@v2
        with:
          results_file: results.json
          results_format: json
          publish_results: true

👉 O parâmetro publish_results: true permite publicar os resultados no OpenSSF Scorecard Dashboard.

💾 4. Resultado no Painel OpenSSF

O resultado da análise pode ser visualizado publicamente no Scorecard Dashboard. Basta pesquisar pelo nome do repositório.

Exemplo:
	•	https://deps.dev/scorecard/github.com/ossf/scorecard

🔒 5. Boas Práticas Recomendadas pelo Scorecard

✅ Ative a proteção de branch (branch protection) no GitHub.
✅ Use MFA para todos os colaboradores.
✅ Revise o código antes do merge (pull request reviews).
✅ Fixe as versões das dependências para evitar atualizações inesperadas.
✅ Use workflows seguros e restrinja permissões de tokens.
✅ Documente a política de segurança no arquivo SECURITY.md.
✅ Faça releases assinados digitalmente.

🚀 6. Integração com Pipelines de CI/CD

O Scorecard pode ser integrado ao pipeline de CI/CD em ambientes como GitHub Actions, GitLab CI/CD ou Jenkins, garantindo que os padrões de segurança sejam monitorados continuamente.

Exemplo em Jenkins:

pipeline {
    agent any
    stages {
        stage('Run Scorecard') {
            steps {
                sh 'scorecard --repo=https://github.com/org/repo'
            }
        }
    }
}

Se quiser, posso criar um workflow de GitHub Actions usando o Scorecard para o seu projeto de backend em Express.js. 🚀🛡️