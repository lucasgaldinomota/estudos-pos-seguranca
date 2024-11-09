# Docker Registry

Um **Docker Registry** é um repositório que armazena e distribui imagens Docker. É um local centralizado onde você pode armazenar, versionar e compartilhar suas imagens Docker. O Docker Registry pode ser público ou privado.

### Tipos de Docker Registries:

1. **Docker Hub**:
   - O **Docker Hub** é o registro de imagens mais popular e é mantido pela Docker, Inc. É um serviço público e privado onde você pode encontrar imagens Docker prontas para uso, além de hospedar suas próprias imagens.
   - **URL**: [hub.docker.com](https://hub.docker.com/)

2. **Docker Registry Privado**:
   - Você também pode configurar seu próprio Docker Registry privado, permitindo que apenas sua equipe ou organização acesse as imagens. Isso é útil para controlar a distribuição de imagens sensíveis e privadas.
   - A Docker oferece uma implementação de código aberto chamada **Docker Distribution** que pode ser usada para criar seu próprio registro privado.

### Como Funciona o Docker Registry?

- **Imagens Docker**: Quando você cria uma imagem Docker a partir de um `Dockerfile`, você pode armazená-la em um registry. As imagens podem ser versionadas usando tags, o que permite que diferentes versões de uma imagem sejam armazenadas e recuperadas.
- **Pull e Push**: 
  - **Pull**: Quando você deseja usar uma imagem, você executa o comando `docker pull <nome da imagem>` para baixá-la de um registro.
  - **Push**: Quando você cria uma nova imagem ou atualiza uma existente, você pode fazer o "push" dessa imagem para o registry usando o comando `docker push <nome da imagem>`.

### Exemplos de Comandos com Docker Registry:

1. **Login no Docker Hub (registro público)**:
   Para enviar ou baixar imagens do Docker Hub, você precisa estar autenticado. Use o comando:
   ```bash
   docker login
   ```
   Isso solicitará seu nome de usuário e senha do Docker Hub.

2. **Fazer Push de uma Imagem para o Docker Hub**:
   - Primeiro, crie a imagem com o comando `docker build`:
     ```bash
     docker build -t username/nome-da-imagem:tag .
     ```
   - Depois, faça o push para o Docker Hub:
     ```bash
     docker push username/nome-da-imagem:tag
     ```
   - O `username` deve ser o seu nome de usuário no Docker Hub.

3. **Fazer Pull de uma Imagem do Docker Hub**:
   - Para baixar uma imagem pública, use o comando:
     ```bash
     docker pull nome-da-imagem:tag
     ```

4. **Configurar um Docker Registry Privado**:
   Você pode criar um registro privado usando a imagem oficial do Docker Registry. Aqui está um exemplo de como executar um registro privado local:
   ```bash
   docker run -d -p 5000:5000 --name registry registry:2
   ```
   - Isso inicia um registry privado local na porta 5000.

   Para fazer push de uma imagem para o seu registry privado:
   - Marque a imagem com o nome do registro:
     ```bash
     docker tag nome-da-imagem localhost:5000/nome-da-imagem
     ```
   - Faça o push para o registry privado:
     ```bash
     docker push localhost:5000/nome-da-imagem
     ```

### Vantagens de Usar um Docker Registry:

1. **Compartilhamento de Imagens**: Facilita o compartilhamento de imagens entre desenvolvedores e equipes.
2. **Automação**: Integrar o Docker Registry em pipelines de CI/CD ajuda a automatizar a construção e distribuição de imagens Docker.
3. **Controle de Versão**: As imagens podem ser versionadas usando tags (por exemplo, `v1.0`, `latest`), o que facilita o controle de versões da sua aplicação.
4. **Segurança**: Ao configurar um registro privado, você pode garantir que apenas usuários autorizados tenham acesso às imagens, o que melhora a segurança.

### Docker Registry vs Docker Hub:
- **Docker Hub**: Serviço público e popular com uma vasta coleção de imagens Docker prontas para uso.
- **Docker Registry Privado**: Ideal para organizações que precisam de controle total sobre suas imagens, especialmente quando elas contêm informações sensíveis ou precisam ser restritas a um grupo específico de pessoas.

### Considerações de Segurança:
- Ao usar registros privados, você pode implementar autenticação básica e TLS (Transport Layer Security) para criptografar as conexões.
- Além disso, você pode controlar quem pode fazer push ou pull de imagens através de permissões.

Com isso, o Docker Registry oferece uma maneira eficiente e segura de armazenar, compartilhar e distribuir suas imagens Docker, tanto em um ambiente privado quanto público.