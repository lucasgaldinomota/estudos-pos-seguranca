# Dependency Confusion

**Dependency Confusion** é um tipo de ataque de cadeia de suprimentos de software que explora a maneira como gerenciadores de pacotes e sistemas de build resolvem dependências em projetos de software. Esse ataque tira proveito da diferença entre dependências privadas (internas) e públicas (externas) para injetar código malicioso em aplicações que dependem desses pacotes.

### Como Funciona o Ataque de Dependency Confusion

O ataque de Dependency Confusion ocorre quando um sistema de build (como npm, PyPI, Maven, etc.) prioriza um pacote de dependência pública malicioso em vez de um pacote de dependência interna legítima. Isso pode acontecer se um desenvolvedor configurar o sistema de build de forma incorreta ou se o sistema de gerenciamento de pacotes procurar automaticamente por pacotes em repositórios públicos.

#### Passos do Ataque:

1. **Identificação de Dependências Internas**:
   - O atacante descobre nomes de pacotes internos usados por uma organização, geralmente por meio de engenharia social, análise de código público, ou técnicas de scraping.

2. **Registro de Pacotes Públicos com Nomes Similares**:
   - O atacante cria um pacote público em um repositório público (como npm, PyPI, RubyGems, etc.) usando o mesmo nome de uma dependência interna da organização alvo.
   
3. **Injeção de Código Malicioso**:
   - O atacante inclui código malicioso no pacote público que foi criado, projetado para ser executado automaticamente quando o pacote for baixado e instalado.

4. **Confusão de Dependência**:
   - Quando o sistema de build ou gerenciamento de pacotes da organização alvo tenta resolver a dependência, ele pode acabar baixando o pacote público malicioso, pensando que é o pacote interno legítimo.

5. **Execução de Código Malicioso**:
   - O código malicioso injetado no pacote é executado no ambiente da vítima, potencialmente comprometendo o sistema, roubando informações, ou realizando outras atividades maliciosas.

### Exemplos de Ataques de Dependency Confusion

- **Caso de Alex Birsan (2021)**: Este é o ataque de Dependency Confusion mais notável. Alex Birsan, um pesquisador de segurança, encontrou nomes de pacotes internos usados por grandes empresas como Apple, Microsoft, Tesla, e Uber. Ele registrou pacotes públicos com os mesmos nomes e incluiu código para notificar sua execução. Surpreendentemente, muitos sistemas de build corporativos baixaram e executaram os pacotes públicos em vez dos internos.

### Medidas de Prevenção contra Dependency Confusion

1. **Configuração Correta de Repositórios de Pacotes**:
   - Configure seus gerenciadores de pacotes (como npm, pip, Maven, etc.) para priorizar pacotes internos e bloquear a resolução automática de dependências em repositórios públicos quando uma versão interna estiver disponível.

2. **Uso de Registries Privados**:
   - Utilize registries privados para armazenar e gerenciar dependências internas e configurar seus ambientes para nunca buscar pacotes com nomes correspondentes em registries públicos.

3. **Políticas de Nomeação e Controle de Versão**:
   - Evite nomes de pacotes internos que sejam muito genéricos ou fáceis de adivinhar. Use namespaces organizacionais exclusivos para pacotes internos e controle estritamente as versões publicadas.

4. **Monitoramento e Auditoria de Dependências**:
   - Implemente ferramentas de monitoramento para detectar pacotes recém-instalados ou atualizados e auditorias regulares para garantir que pacotes externos não sejam substituídos por variantes internas.

5. **Assinatura de Pacotes e Verificação de Integridade**:
   - Use assinaturas digitais e hashes para verificar a integridade dos pacotes antes de instalá-los. Isso assegura que o pacote não tenha sido adulterado.

6. **Educação e Treinamento**:
   - Treine desenvolvedores e equipes de DevOps sobre os riscos associados ao Dependency Confusion e as melhores práticas para evitar esses ataques.

### Conclusão

**Dependency Confusion** é uma ameaça crescente em ambientes de desenvolvimento modernos, especialmente com o uso generalizado de pacotes públicos e internos. Adotar práticas de segurança robustas e configurar corretamente os ambientes de build e gerenciamento de pacotes são passos essenciais para mitigar esse tipo de ataque. É fundamental que as organizações mantenham um controle rigoroso sobre suas dependências e fiquem atentas a qualquer comportamento incomum ou inesperado em seus sistemas de build.