# PCI DSS

O que é PCI DSS?

O PCI DSS (Payment Card Industry Data Security Standard) é um padrão global de segurança para proteger dados de cartões de pagamento. Ele foi criado pelo PCI Security Standards Council (PCI SSC), que inclui grandes empresas como Visa, MasterCard, American Express, Discover e JCB.

Esse padrão define requisitos obrigatórios para qualquer empresa que processe, armazene ou transmita informações de cartões de crédito, garantindo a segurança dos dados e reduzindo riscos de fraudes.

2. Principais Requisitos do PCI DSS

O PCI DSS possui 12 requisitos principais, organizados em 6 categorias:

1. Construir e Manter uma Rede Segura

✅ (1) Usar firewalls para proteger dados do titular do cartão
✅ (2) Não usar senhas padrão e configurações de fábrica

2. Proteger Dados do Titular do Cartão

✅ (3) Proteger os dados armazenados (exemplo: criptografia)
✅ (4) Criptografar a transmissão de dados sensíveis

3. Manter um Programa de Gestão de Vulnerabilidades

✅ (5) Usar antivírus atualizado em todos os dispositivos críticos
✅ (6) Desenvolver e manter sistemas e aplicações seguras

4. Implementar Medidas Fortes de Controle de Acesso

✅ (7) Restringir o acesso aos dados do cartão com base na necessidade de negócio
✅ (8) Identificar e autenticar o acesso aos sistemas (exemplo: MFA)
✅ (9) Restringir o acesso físico aos dados do cartão

5. Monitorar e Testar Redes Regularmente

✅ (10) Monitorar e registrar todos os acessos aos dados e sistemas de pagamento
✅ (11) Testar regularmente sistemas e processos de segurança

6. Ter uma Política de Segurança da Informação

✅ (12) Implementar e manter uma política de segurança

3. Como PCI DSS Impacta Ambientes de CI/CD?

Em ambientes de CI/CD, o PCI DSS exige que as práticas de segurança sejam aplicadas a todo o ciclo de desenvolvimento, incluindo:

1️⃣ Proteção de Dados Sensíveis
	•	Evitar armazenar dados de cartão em repositórios (código, logs ou banco de dados).
	•	Usar variáveis de ambiente seguras para armazenar credenciais.
	•	Criptografar dados em trânsito e em repouso (TLS, AES-256, etc.).

2️⃣ Controle de Acesso ao Pipeline
	•	Restringir acesso aos pipelines para evitar deploys inseguros.
	•	Autenticação forte (MFA) para acessar CI/CD e repositórios.
	•	Aplicar princípio do menor privilégio em usuários e serviços.

3️⃣ Gestão de Vulnerabilidades e Monitoramento
	•	Fazer scan de código regularmente com ferramentas como SonarQube, Snyk, Trivy.
	•	Monitorar logs de execução do CI/CD para detectar atividades suspeitas.
	•	Realizar testes de segurança automatizados (exemplo: DAST, SAST).

4️⃣ Segurança na Entrega e Deploys
	•	Assinar digitalmente artefatos e imagens de containers.
	•	Garantir que o ambiente de produção seja seguro e segregado do ambiente de desenvolvimento.
	•	Implementar hardening em servidores e containers usados no pipeline.

4. Conformidade e Auditoria

Empresas que processam pagamentos precisam realizar auditorias de conformidade PCI DSS, que podem incluir:
🔍 Scan de vulnerabilidades trimestral por uma empresa certificada.
📜 Auditorias anuais para validar conformidade.
🔐 Treinamento contínuo da equipe de desenvolvimento e segurança.