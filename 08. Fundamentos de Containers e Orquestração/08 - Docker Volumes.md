# Docker Volumes

**Docker Volumes** são uma maneira de persistir dados em containers Docker. Ao contrário dos sistemas de arquivos temporários usados dentro de containers, os volumes são armazenados fora do contêiner e podem ser compartilhados entre múltiplos containers. Eles são especialmente úteis para armazenar dados que precisam sobreviver à reinicialização do contêiner ou ao seu término, como bancos de dados, arquivos de configuração, e logs.

### Características dos Volumes:

1. **Persistência de Dados**:
   - Os volumes são armazenados em um local fora do contêiner, geralmente no sistema de arquivos do host, garantindo que os dados não sejam perdidos quando o contêiner é removido ou recriado.

2. **Isolamento**:
   - Volumes permitem que os dados sejam isolados do contêiner, ou seja, você pode modificar os dados sem afetar diretamente o contêiner.

3. **Facilidade de Backup e Recuperação**:
   - Como os volumes estão fora do contêiner, é fácil fazer backups e restaurar dados importantes.

4. **Compartilhamento de Dados**:
   - Vários contêineres podem compartilhar o mesmo volume, o que é útil quando você precisa que múltiplos contêineres acessem os mesmos dados.

5. **Performance**:
   - Os volumes são otimizados para desempenho e fornecem uma melhor performance em comparação com o uso de bind mounts (que montam diretamente diretórios do sistema de arquivos do host).

### Tipos de Armazenamento com Docker:

1. **Volumes**:
   - Armazenados no sistema de arquivos do Docker no host. O Docker gerencia esses volumes e eles podem ser compartilhados entre múltiplos contêineres. Eles são ideais para persistência de dados e compartilhamento entre contêineres.
   
2. **Bind Mounts**:
   - São diretórios ou arquivos do sistema de arquivos do host montados diretamente dentro do contêiner. Embora ofereçam flexibilidade, eles não são tão portáveis ou seguros quanto volumes.

3. **tmpfs Mounts**:
   - Armazenam dados na memória temporária do host. São úteis para dados temporários que não precisam ser persistidos.

### Comandos Comuns para Trabalhar com Volumes:

1. **Criar um Volume**:
   ```bash
   docker volume create nome-do-volume
   ```

2. **Listar Volumes**:
   ```bash
   docker volume ls
   ```

3. **Inspecionar um Volume**:
   ```bash
   docker volume inspect nome-do-volume
   ```
   Isso exibe informações detalhadas sobre o volume, como o caminho no sistema de arquivos do host e onde ele está montado.

4. **Remover um Volume**:
   ```bash
   docker volume rm nome-do-volume
   ```
   **Nota**: Volumes só podem ser removidos se não estiverem em uso por nenhum contêiner.

5. **Usar um Volume em um Contêiner**:
   Para montar um volume dentro de um contêiner, você pode usar a opção `-v` ou `--mount` no comando `docker run`:
   
   **Exemplo 1 (usando `-v`)**:
   ```bash
   docker run -v nome-do-volume:/caminho/no/container nome-da-imagem
   ```

   **Exemplo 2 (usando `--mount`)**:
   ```bash
   docker run --mount source=nome-do-volume,target=/caminho/no/container nome-da-imagem
   ```
   Ambos os comandos montam o volume `nome-do-volume` no caminho especificado dentro do contêiner.

6. **Remover Volumes Não Usados**:
   Para limpar volumes que não estão mais em uso por nenhum contêiner, você pode usar:
   ```bash
   docker volume prune
   ```

### Usando Volumes com Docker Compose:

No **Docker Compose**, volumes são definidos no arquivo `docker-compose.yml` e podem ser montados em contêineres de forma similar ao comando `docker run`.

**Exemplo de arquivo `docker-compose.yml` com volumes**:

```yaml
version: '3'
services:
  app:
    image: my-app
    volumes:
      - my-volume:/app/data
volumes:
  my-volume:
```

Esse exemplo cria um volume chamado `my-volume` e o monta no caminho `/app/data` dentro do contêiner `app`.

### Vantagens do Uso de Volumes:
1. **Persistência**: Os volumes permitem que dados persistam após a remoção ou recriação dos contêineres.
2. **Facilidade de Backup e Recuperação**: Com volumes, é fácil fazer backup ou restaurar dados.
3. **Compartilhamento de Dados**: Vários contêineres podem compartilhar o mesmo volume, tornando-o útil em aplicativos que exigem acesso a dados compartilhados.
4. **Desempenho**: Volumes são otimizados para armazenamento de dados e podem oferecer melhor desempenho do que bind mounts.

### Considerações:
- **Segurança**: Volumes são mais seguros que bind mounts, pois são isolados do sistema de arquivos do host.
- **Portabilidade**: Como volumes são gerenciados pelo Docker, eles são mais portáveis entre diferentes ambientes de contêiner.

Os **Docker Volumes** são fundamentais para gerenciar dados persistentes em contêineres, tornando-os uma parte importante da infraestrutura Docker em ambientes de produção.