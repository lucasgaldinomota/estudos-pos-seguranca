# Dockerfile

Um **Dockerfile** é um arquivo de texto usado para definir as instruções que um **Docker** deve seguir para construir uma imagem. Ele especifica os passos necessários para instalar e configurar um ambiente de software dentro de um contêiner.

Aqui está um exemplo básico de um **Dockerfile** e uma explicação de cada linha:

### Exemplo de Dockerfile:
```dockerfile
# Use uma imagem base oficial do Node.js
FROM node:14

# Defina o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copie o package.json e package-lock.json para o contêiner
COPY package*.json ./

# Instale as dependências do projeto
RUN npm install

# Copie o código-fonte para dentro do contêiner
COPY . .

# Exponha a porta que a aplicação usará
EXPOSE 3000

# Comando para iniciar a aplicação
CMD ["npm", "start"]
```

### Explicação das instruções:

1. **FROM**:
   - Define a imagem base para o contêiner. Neste caso, estamos usando a imagem oficial do Node.js na versão 14.

2. **WORKDIR**:
   - Define o diretório de trabalho dentro do contêiner. Qualquer comando subsequente será executado a partir desse diretório.

3. **COPY**:
   - A primeira instrução `COPY package*.json ./` copia os arquivos `package.json` e `package-lock.json` para o diretório de trabalho no contêiner. Isso é útil para instalar as dependências antes de copiar o restante dos arquivos, permitindo que o cache do Docker seja utilizado eficientemente.

4. **RUN**:
   - Executa um comando no contêiner. Neste caso, `RUN npm install` instala as dependências do projeto.

5. **EXPOSE**:
   - Informa ao Docker que o contêiner escutará na porta especificada. No caso do Node.js, isso é normalmente a porta 3000.

6. **CMD**:
   - Define o comando que será executado quando o contêiner for iniciado. Aqui, estamos usando `npm start` para iniciar a aplicação Node.js.

### Como construir e rodar a imagem com o Dockerfile:

1. **Construir a imagem**:
   No terminal, execute o comando abaixo no mesmo diretório onde o Dockerfile está localizado:
   ```bash
   docker build -t nome-da-imagem .
   ```

2. **Rodar o contêiner**:
   Após construir a imagem, você pode rodar um contêiner com:
   ```bash
   docker run -p 3000:3000 nome-da-imagem
   ```
   Esse comando mapeia a porta 3000 do contêiner para a porta 3000 da máquina host, permitindo que você acesse a aplicação.

### Outras Instruções Comuns no Dockerfile:

- **ENV**: Define variáveis de ambiente.
- **ADD**: Similar ao `COPY`, mas também pode extrair arquivos de um arquivo tar.
- **ENTRYPOINT**: Define um comando que sempre será executado quando o contêiner for iniciado.
- **USER**: Define o usuário que será usado para executar o contêiner.
- **ARG**: Define variáveis de build que podem ser passadas durante a construção da imagem.

### Exemplo de Dockerfile com Variáveis de Ambiente:
```dockerfile
FROM node:14

# Defina uma variável de ambiente
ENV NODE_ENV=production

WORKDIR /app
COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000
CMD ["npm", "start"]
```

Esse é um exemplo básico, mas o Dockerfile pode ser muito mais complexo, dependendo das necessidades da aplicação e do ambiente.