# Docker Ignore

O arquivo **`.dockerignore`** é usado para especificar quais arquivos e diretórios **não devem ser incluídos** na construção de uma imagem Docker. Isso é útil para evitar que arquivos desnecessários ou confidenciais sejam adicionados à imagem, o que pode aumentar o tamanho da imagem ou expor informações sensíveis.

### Estrutura e Sintaxe do `.dockerignore`:

A sintaxe do arquivo **`.dockerignore`** é semelhante ao `.gitignore`, e ele segue padrões específicos de exclusão de arquivos.

#### Exemplo básico de um `.dockerignore`:
```plaintext
# Ignorar arquivos de log
*.log

# Ignorar diretórios de backup
backup/

# Ignorar arquivos de configuração local
config/local.json

# Ignorar arquivos temporários
tmp/
```

### Como Funciona:

1. **Padrões globais**:
   - `*`: Corresponde a qualquer sequência de caracteres.
   - `?`: Corresponde a um único caractere.
   - `**/`: Corresponde a qualquer subdiretório.

2. **Comentários**:
   - Comentários podem ser adicionados precedendo a linha com `#`.

3. **Exclusões**:
   - Para excluir arquivos ou pastas específicos, você pode usar a barra (`/`):
     - `path/to/file` vai excluir o arquivo ou pasta `file` no caminho especificado.
   
4. **Inclusões**:
   - Você pode reverter uma exclusão com o prefixo `!`, permitindo que certos arquivos ou pastas sejam incluídos mesmo que uma regra anterior tenha os excluído.
   - Exemplo:
     ```plaintext
     *.log
     !important.log
     ```
     Isso vai ignorar todos os arquivos `.log`, exceto o `important.log`.

### Exemplo Completo de `.dockerignore`:
```plaintext
# Ignorar arquivos de sistema
.DS_Store
Thumbs.db

# Ignorar arquivos de configuração local
config/dev.json
config/*.yml

# Ignorar diretórios temporários e de cache
tmp/
.cache/

# Ignorar diretórios e arquivos de versão controlada
.git/
.gitignore
Dockerfile
```

### Benefícios de Usar `.dockerignore`:

1. **Reduz o Tamanho da Imagem**:
   - Ao evitar a inclusão de arquivos desnecessários, como logs e arquivos temporários, a imagem Docker se torna menor e mais eficiente.

2. **Melhora a Segurança**:
   - Impede que arquivos confidenciais, como chaves privadas ou configurações sensíveis, sejam adicionados à imagem Docker.

3. **Aumenta a Performance**:
   - Reduz a quantidade de arquivos que o Docker precisa analisar durante o processo de construção da imagem, o que pode acelerar o tempo de build.

### Como Usar:

Quando você executa o comando `docker build`, o Docker automaticamente verifica o arquivo `.dockerignore` no diretório onde o `Dockerfile` está localizado e usa as regras para excluir os arquivos mencionados na construção da imagem.

```bash
docker build -t minha-imagem .
```

Neste comando, o Docker irá ignorar os arquivos e diretórios definidos no `.dockerignore`, garantindo que apenas o necessário seja incluído na imagem.