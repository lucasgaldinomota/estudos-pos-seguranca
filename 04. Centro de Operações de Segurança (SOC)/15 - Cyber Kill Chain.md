# Cyber Kill Chain

A "Cyber Kill Chain" é um modelo desenvolvido pela Lockheed Martin que descreve as etapas que os adversários cibernéticos seguem para realizar um ataque. Este modelo ajuda as organizações a entenderem as fases de um ataque cibernético e a desenvolverem estratégias de defesa para detectar, prevenir e mitigar esses ataques em cada estágio.

Aqui estão as sete etapas da Cyber Kill Chain:

1. **Reconhecimento (Reconnaissance)**:
   - Nesta fase, o atacante coleta informações sobre o alvo. Isso pode incluir a pesquisa de funcionários, identificando vulnerabilidades em sistemas, e coletando dados sobre a rede e infraestrutura.
   - Defesas: Implementar práticas de segurança para proteger informações públicas, usar honeypots para detectar reconhecimento, monitorar logs de acesso.

2. **Armamento (Weaponization)**:
   - O atacante cria uma carga maliciosa (malware) para explorar uma vulnerabilidade específica no sistema do alvo. Isso pode incluir a criação de documentos maliciosos ou a construção de kits de exploração.
   - Defesas: Utilizar sandboxing para analisar arquivos suspeitos, manter um inventário atualizado de software.

3. **Entrega (Delivery)**:
   - O atacante entrega a carga maliciosa ao alvo. Isso pode ser feito através de e-mails de phishing, downloads drive-by, mídia removível ou outros métodos.
   - Defesas: Implementar filtros de e-mail, treinar usuários para reconhecer e-mails de phishing, usar gateways de segurança.

4. **Exploração (Exploitation)**:
   - A carga maliciosa é executada no sistema do alvo, explorando uma vulnerabilidade específica. Isso pode permitir que o atacante obtenha acesso inicial ao sistema.
   - Defesas: Manter sistemas e software atualizados, utilizar soluções de endpoint protection, configurar sistemas para minimizar privilégios.

5. **Instalação (Installation)**:
   - O malware instala uma porta dos fundos (backdoor) ou outra persistência no sistema comprometido, permitindo ao atacante manter o acesso ao sistema.
   - Defesas: Usar software de detecção e resposta de endpoint (EDR), implementar listas de controle de acesso, monitorar instalações de software não autorizadas.

6. **Comando e Controle (Command and Control - C2)**:
   - O malware estabelece um canal de comunicação com o servidor de comando e controle do atacante, permitindo que ele envie comandos ao sistema comprometido.
   - Defesas: Monitorar e bloquear tráfego de rede suspeito, usar análise de comportamento para detectar comunicações anômalas, implementar proxies e firewalls.

7. **Ações sobre Objetivos (Actions on Objectives)**:
   - O atacante executa as ações finais para atingir seus objetivos, como roubo de dados, destruição de informações, ou movimentação lateral para comprometer outros sistemas.
   - Defesas: Implementar monitoramento contínuo, usar ferramentas de detecção de intrusão, realizar auditorias regulares de segurança, ter um plano de resposta a incidentes.

Ao entender e implementar medidas de defesa em cada fase da Cyber Kill Chain, as organizações podem melhorar significativamente suas capacidades de detecção e resposta a ataques cibernéticos, reduzindo a probabilidade de sucesso de um adversário.