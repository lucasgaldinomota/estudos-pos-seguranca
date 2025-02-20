# Autenticação SCM

Autenticação SCM (Source Code Management)

A autenticação SCM refere-se aos métodos usados para garantir que apenas usuários e sistemas autorizados possam acessar repositórios de código-fonte em plataformas como GitHub, GitLab, Bitbucket, Azure DevOps, entre outras. Ela é essencial para proteger o ciclo de desenvolvimento, especialmente em ambientes de CI/CD e em conformidade com normas como PCI DSS.

1. Métodos de Autenticação em SCM

✅ 1.1 Autenticação por Usuário e Senha (Depreciado)
	•	Métodos tradicionais de login usando nome de usuário e senha estão sendo substituídos devido a vulnerabilidades.
	•	Exemplo: GitHub não aceita mais autenticação via senha para operações Git.

🔑 1.2 Autenticação com Tokens de Acesso Pessoal (PAT)
	•	O que é: Tokens gerados pelo SCM para autenticação sem expor senhas.
	•	Benefícios:
	•	Acesso granular (ex.: somente leitura ou escrita).
	•	Tokens expiram automaticamente, aumentando a segurança.
	•	Exemplo: GitHub Personal Access Token (PAT), GitLab Access Token.

Exemplo de uso com Git:

git clone https://<TOKEN>@github.com/usuario/repo.git

🔒 1.3 SSH (Secure Shell Protocol)
	•	O que é: Método seguro usando pares de chaves pública e privada.
	•	Benefícios:
	•	Autenticação sem senha.
	•	Mais seguro para automações, pipelines de CI/CD e acesso remoto.

Exemplo de configuração:

ssh-keygen -t ed25519 -C "seu-email@example.com"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub  # Adicione essa chave no SCM
git clone git@github.com:usuario/repo.git

📦 1.4 Autenticação para CI/CD (Deploy Keys e Tokens de Máquina)
	•	Deploy Keys: Chaves SSH específicas para pipelines de CI/CD com acesso restrito.
	•	Tokens de Máquina: Tokens específicos para integrações automáticas, sem expor credenciais pessoais.
	•	Exemplo:
	•	GitHub Actions usa secrets.GITHUB_TOKEN para autenticar automaticamente.
	•	GitLab CI/CD usa $CI_JOB_TOKEN para acessar projetos internos.

GitHub Actions com Token:

steps:
  - name: Checkout código
    uses: actions/checkout@v4
    with:
      token: ${{ secrets.GITHUB_TOKEN }}

🔐 1.5 Single Sign-On (SSO) com Provedores de Identidade
	•	O que é: Integração com serviços de autenticação como Okta, Azure AD, Google Workspace.
	•	Benefícios:
	•	Gerenciamento centralizado de usuários.
	•	Autenticação multifator (MFA).
	•	Conformidade com requisitos de segurança (ex.: PCI DSS, ISO 27001).

2. Boas Práticas de Segurança para Autenticação SCM

✅ Use MFA (Autenticação Multifator) para todos os acessos humanos.
✅ Prefira tokens ou SSH em vez de senhas tradicionais.
✅ Restrinja permissões com o princípio de menor privilégio.
✅ Armazene tokens e chaves em cofres de segredos (ex.: AWS Secrets Manager, HashiCorp Vault).
✅ Audite e revogue acessos inativos regularmente.

Se precisar de um guia prático para configurar autenticação SCM no seu projeto de CI/CD, posso fornecer exemplos específicos para GitHub, GitLab ou Bitbucket. 🚀🔒