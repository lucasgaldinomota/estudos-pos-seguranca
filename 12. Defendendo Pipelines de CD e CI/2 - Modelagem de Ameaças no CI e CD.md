# Modelagem de ameaças no ambiente de CI/CD 

A modelagem de ameaças no ambiente de CI/CD (Continuous Integration/Continuous Deployment) é essencial para identificar e mitigar riscos que podem comprometer a segurança do pipeline de desenvolvimento.

1. O que é Modelagem de Ameaças no CI/CD?

É o processo de identificar possíveis vulnerabilidades, avaliar seus impactos e definir contramedidas para reduzir riscos de segurança no pipeline.

2. Principais Ameaças no CI/CD

1. Comprometimento do Código-Fonte
	•	Ameaça: Código malicioso inserido no repositório (exemplo: backdoors, malwares, hardcoded credentials).
	•	Mitigação:
	•	Uso de branches protegidos e aprovação obrigatória de PRs.
	•	Escaneamento de código com ferramentas como SonarQube, Semgrep ou CodeQL.
	•	Monitoramento de commits suspeitos.

2. Vazamento de Credenciais e Segredos
	•	Ameaça: Exposição acidental de chaves API, tokens ou credenciais nos repositórios.
	•	Mitigação:
	•	Uso de cofres de segredos (ex: HashiCorp Vault, AWS Secrets Manager).
	•	Implementação de scanners de credenciais como TruffleHog ou GitLeaks.
	•	Nunca armazenar credenciais diretamente no código-fonte.

3. Dependências Comprometidas
	•	Ameaça: Uso de pacotes de terceiros com vulnerabilidades ou dependências maliciosas.
	•	Mitigação:
	•	Uso de ferramentas de análise de dependências (ex: OWASP Dependency-Check, Snyk, Dependabot).
	•	Auditoria e versionamento cuidadoso de pacotes de terceiros.
	•	Preferência por repositórios internos ou artefatos assinados.

4. Build e Deploy Comprometidos
	•	Ameaça: Execução de código malicioso durante o build/deploy por agentes inseguros.
	•	Mitigação:
	•	Isolamento do ambiente de CI/CD, evitando que tenha acesso direto a sistemas críticos.
	•	Uso de execução mínima de privilégios, aplicando o conceito de least privilege.
	•	Verificação de logs e auditorias regulares.

5. Ataques de Supply Chain
	•	Ameaça: Inserção de código malicioso por meio de pacotes ou comprometimento de fornecedores.
	•	Mitigação:
	•	Uso de assinaturas digitais e verificações de integridade em artefatos.
	•	Implementação de SBOM (Software Bill of Materials) para rastrear todas as dependências utilizadas.

6. Execução de Pipelines por Usuários Maliciosos
	•	Ameaça: Atacantes explorando configurações incorretas para rodar código arbitrário.
	•	Mitigação:
	•	Controle de quem pode acionar pipelines.
	•	Limitação de permissões em runners/agents.
	•	Implementação de autenticação forte (MFA) e logs de auditoria.

3. Boas Práticas para Proteger o CI/CD

✅ Segregação de Ambientes: Build, testes e deploy devem rodar em ambientes isolados.
✅ MFA e Gerenciamento de Acessos: Apenas usuários autorizados devem ter acesso ao pipeline.
✅ Monitoramento Contínuo: Logs de CI/CD devem ser analisados regularmente.
✅ Proteção de Artefatos: Pacotes e imagens Docker devem ser verificados antes do uso.
✅ Hardening de Runners: Agents do CI/CD devem rodar em ambientes seguros e monitorados.