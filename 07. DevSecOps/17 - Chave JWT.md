# Chave JWT

Uma **chave JWT (JSON Web Token)** é uma parte essencial da infraestrutura de segurança usada para gerar e validar tokens JWT, que são amplamente utilizados para autenticação e autorização em aplicações web e APIs.

### O que é um JWT?

O JWT (JSON Web Token) é um padrão aberto (RFC 7519) para representar claims (afirmações) de forma compacta e segura entre partes. Um JWT é composto por três partes codificadas em Base64:

1. **Header (Cabeçalho)**:
   - Contém informações sobre o tipo de token (geralmente "JWT") e o algoritmo de assinatura usado (por exemplo, HMAC SHA256, RSA).

2. **Payload (Carga Útil)**:
   - Contém as claims ou dados do token, como informações sobre o usuário e permissões. As claims podem ser registradas (predefinidas), públicas ou privadas.

3. **Signature (Assinatura)**:
   - É a parte que garante a integridade do token e a verificação de sua autenticidade. A assinatura é gerada usando o cabeçalho e a carga útil, e uma chave secreta ou par de chaves.

### Tipos de Chaves JWT:

1. **Chave Secreta (Symmetric Key)**:
   - **Descrição**: Usada em algoritmos de assinatura simétricos como HMAC SHA256 (HS256). A mesma chave é usada para assinar e validar o JWT.
   - **Exemplo de Algoritmo**: HS256, HS384, HS512.
   - **Uso**: Adequada para ambientes onde a chave pode ser mantida em segredo entre as partes (como um servidor backend).

2. **Chave Pública/Privada (Asymmetric Key)**:
   - **Descrição**: Usada em algoritmos de assinatura assimétricos como RSA ou ECDSA. Uma chave privada é usada para assinar o JWT, e a chave pública é usada para validar a assinatura.
   - **Exemplo de Algoritmo**: RS256, RS384, RS512, ES256, ES384, ES512.
   - **Uso**: Adequada para ambientes onde a chave pública pode ser compartilhada amplamente, enquanto a chave privada é mantida em segredo.

### Como Funciona a Assinatura JWT:

1. **Criação do Token**:
   - O servidor gera o JWT com o cabeçalho e a carga útil e o assina usando uma chave secreta ou um par de chaves.

2. **Validação do Token**:
   - Quando o token é recebido, o receptor usa a mesma chave secreta (para algoritmos simétricos) ou a chave pública correspondente (para algoritmos assimétricos) para validar a assinatura e garantir que o token não foi alterado.

### Segurança da Chave JWT:

- **Chave Secreta**: Deve ser mantida segura e nunca exposta publicamente. A segurança do JWT depende da confidencialidade desta chave.
- **Chave Privada**: Deve ser protegida rigorosamente para evitar que seja comprometida. A chave pública pode ser distribuída, mas a chave privada deve permanecer segura.

### Exemplos de Uso:

- **Autenticação**: Após um usuário fazer login, um servidor pode emitir um JWT contendo informações sobre o usuário e permissões. O cliente armazena o token e o envia em cada solicitação subsequente para autenticação.
- **Autorização**: O JWT pode conter claims sobre permissões do usuário, que são usadas pelo servidor para verificar se o usuário tem acesso a determinados recursos.

### Benefícios do JWT:

- **Compacto**: Os tokens são compactos e podem ser transmitidos facilmente em URLs, cabeçalhos HTTP ou como parâmetros de consulta.
- **Autocontido**: Contém todas as informações necessárias para a autenticação e autorização, evitando a necessidade de consulta adicional a um banco de dados.

### Limitações do JWT:

- **Tamanho do Token**: Se o payload for grande, o JWT pode se tornar consideravelmente grande, o que pode afetar o desempenho.
- **Expiração**: O JWT pode ser comprometido se não for configurado corretamente com um tempo de expiração adequado.

Em resumo, a **chave JWT** é crucial para garantir a integridade e a autenticidade dos tokens JWT. Dependendo do tipo de algoritmo de assinatura usado, pode ser uma chave secreta compartilhada ou um par de chaves pública/privada. É importante gerenciar essas chaves com segurança para proteger a aplicação contra possíveis ataques e vazamentos.