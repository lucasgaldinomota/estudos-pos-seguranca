# SAST

**SAST** (Static Application Security Testing), ou Teste de Segurança de Aplicação Estática, é uma técnica de análise de segurança que examina o código-fonte de um software em busca de vulnerabilidades de segurança, sem executar o código. É uma abordagem "estática" porque analisa o código "em repouso", ou seja, antes que ele seja compilado e executado.

### Características do SAST:

1. **Análise de Código em Repositório**: O SAST examina o código-fonte, os binários ou os arquivos executáveis de uma aplicação em um repositório, sem a necessidade de executar o software. Isso inclui o código escrito em linguagens de programação como Java, C#, Python, etc.

2. **Detecção de Vulnerabilidades Conhecidas**: O SAST é eficaz na identificação de vulnerabilidades de segurança conhecidas, como injeção de SQL, cross-site scripting (XSS), buffer overflows, uso inseguro de criptografia, e manipulação de entrada inadequada.

3. **Análise Durante o Ciclo de Desenvolvimento**: Pode ser integrado ao ambiente de desenvolvimento integrado (IDE) ou ao pipeline de CI/CD (Continuous Integration/Continuous Deployment) para realizar análises automáticas durante o ciclo de vida de desenvolvimento de software (SDLC), ajudando a identificar e corrigir problemas de segurança mais cedo.

4. **Feedback Rápido**: Fornece feedback quase instantâneo aos desenvolvedores sobre possíveis problemas de segurança, permitindo que eles façam correções antes que o código seja promovido a um ambiente de produção.

5. **Cobertura de Código**: Analisa todo o código de uma aplicação, incluindo caminhos raramente ou nunca executados, o que ajuda a identificar vulnerabilidades que poderiam ser exploradas por um atacante em circunstâncias específicas.

### Benefícios do SAST:

- **Correção Antecipada de Vulnerabilidades**: Permite que as vulnerabilidades sejam identificadas e corrigidas durante a fase de desenvolvimento, o que é geralmente mais barato e menos complexo do que corrigir falhas de segurança em produção.
- **Integração com DevSecOps**: Facilita a integração de práticas de segurança no DevOps (DevSecOps), promovendo uma cultura de "segurança em primeiro lugar".
- **Conformidade com Normas de Segurança**: Ajuda as organizações a cumprir padrões de segurança e regulamentações de conformidade, como o OWASP Top Ten, PCI-DSS, HIPAA, entre outros.
- **Detecção de Vulnerabilidades Sem Necessidade de Executar o Código**: Pode detectar problemas em bibliotecas e dependências de código que nem sempre são facilmente testáveis em um ambiente executável.

### Limitações do SAST:

- **Falsos Positivos**: Pode gerar falsos positivos, o que significa que algumas das vulnerabilidades identificadas podem não ser reais ou relevantes no contexto específico.
- **Cobertura de Vulnerabilidades em Runtime**: Não detecta vulnerabilidades que só aparecem quando o código é executado (por exemplo, problemas de configuração de ambiente ou erros lógicos que dependem de entradas específicas).
- **Complexidade de Configuração e Integração**: Em alguns casos, configurar e manter ferramentas SAST pode ser complexo e requerer ajustes constantes para evitar ruídos na detecção de vulnerabilidades.

Em resumo, o SAST é uma prática essencial de segurança para detectar e corrigir vulnerabilidades de segurança no código-fonte de software o mais cedo possível no ciclo de desenvolvimento, ajudando a melhorar a segurança geral do software antes que ele chegue ao ambiente de produção.