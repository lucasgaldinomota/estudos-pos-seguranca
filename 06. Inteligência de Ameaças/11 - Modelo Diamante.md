# Modelo Diamante de Análise de Intrusão

O Modelo Diamante de Análise de Intrusão é uma metodologia desenvolvida para fornecer uma estrutura sistemática para entender e analisar incidentes de segurança cibernética. Ele foi introduzido em um artigo de 2013 por Caltagirone, Pendergast e Betz. Este modelo ajuda analistas a identificar relações e características de uma intrusão, facilitando a investigação e resposta a incidentes.

#### Estrutura do Modelo Diamante

O modelo é baseado em quatro componentes principais que formam os vértices de um diamante:

1. **Adversário**:
   - Representa o atacante ou grupo de atacantes responsáveis pela intrusão. Envolve identificar quem são, suas motivações, capacidades e objetivos.

2. **Capacidade**:
   - Refere-se às ferramentas, técnicas e procedimentos (TTPs) utilizados pelo adversário para conduzir o ataque. Isso inclui malwares, exploits, ferramentas de exploração, etc.

3. **Infraestrutura**:
   - Inclui os recursos utilizados pelo adversário para lançar e controlar o ataque. Isso pode envolver servidores de comando e controle (C2), domínios, endereços IP, redes sociais, e outras plataformas de comunicação.

4. **Vítima**:
   - Refere-se ao alvo do ataque, que pode ser uma pessoa, organização, sistema ou rede. Identificar a vítima ajuda a entender o contexto do ataque e as potenciais implicações.

### Conexões e Metadados

Além dos quatro vértices, o Modelo Diamante também considera duas conexões importantes:

- **Atividade**: A conexão entre a Capacidade e a Infraestrutura, que mostra como as ferramentas são implantadas.
- **Método**: A conexão entre o Adversário e a Capacidade, destacando as técnicas usadas pelo atacante.
- **Faceta da Vítima**: A conexão entre a Vítima e a Infraestrutura, indicando como a vítima foi alvo e comprometida.
- **Faceta Social-Política**: A ligação entre o Adversário e a Vítima, que pode incluir motivações políticas, sociais ou econômicas.

### Aplicações do Modelo Diamante

1. **Investigação de Incidentes**:
   - Ajuda analistas a identificar rapidamente as várias partes de um ataque e como elas se relacionam. Isso é essencial para determinar a origem do ataque e como ele se espalhou.

2. **Inteligência de Ameaças**:
   - Facilita a coleta e análise de dados sobre ameaças, permitindo a criação de perfis de adversários e o desenvolvimento de estratégias de mitigação mais eficazes.

3. **Compartilhamento de Informações**:
   - Proporciona uma linguagem comum e uma estrutura para compartilhar informações sobre ameaças entre diferentes organizações e setores.

### Exemplos de Uso

- **Ataques APT (Advanced Persistent Threat)**:
  - Um grupo APT específico pode ser identificado (Adversário) usando uma variedade de exploits de dia zero (Capacidade), controlando suas operações a partir de servidores em locais específicos (Infraestrutura), visando redes corporativas de alto valor (Vítima).

- **Campanhas de Phishing**:
  - Um ator de ameaça pode ser reconhecido (Adversário) por sua técnica de phishing (Capacidade), utilizando domínios falsos e servidores C2 (Infraestrutura), visando funcionários de empresas financeiras (Vítima).

### Conclusão

O Modelo Diamante de Análise de Intrusão é uma ferramenta valiosa para a cibersegurança, permitindo uma análise detalhada e estruturada dos incidentes de segurança. Ao decompor um ataque nos seus componentes fundamentais e identificar as conexões entre eles, analistas podem melhorar significativamente suas capacidades de resposta e defesa contra ameaças cibernéticas.

### Referências

- Caltagirone, S., Pendergast, A., & Betz, C. (2013). The Diamond Model of Intrusion Analysis.
- [CrowdStrike](https://www.crowdstrike.com/resources/articles/diamond-model-of-intrusion-analysis/)
- [MITRE ATT&CK](https://attack.mitre.org/)