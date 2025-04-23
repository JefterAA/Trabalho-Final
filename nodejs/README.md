```markdown
# Dockerfile para Node.js

Este arquivo `Dockerfile` é usado para criar uma imagem Docker personalizada para executar uma aplicação Node.js. Ele configura um ambiente de desenvolvimento baseado na versão 22 do Node.js, instala as dependências da aplicação e expõe a porta padrão para execução.

## Contexto

O Node.js é uma plataforma amplamente utilizada para construir aplicações web escaláveis e rápidas. Este `Dockerfile` utiliza a imagem oficial do Node.js na versão 22 e configura o ambiente necessário para executar uma aplicação web. Ele copia os arquivos de dependências, instala os pacotes necessários e define o comando padrão para iniciar a aplicação.

## Estrutura do Dockerfile

1. **Imagem Base**:
   ```dockerfile
   FROM node:22
   ```
   Utiliza a imagem oficial do Node.js na versão 22 como base.

2. **Diretório de Trabalho**:
   ```dockerfile
   WORKDIR /usr/src/app
   ```
   Define o diretório de trabalho dentro do container como `/usr/src/app`.

3. **Cópia de Dependências**:
   ```dockerfile
   COPY ./src/package*.json ./
   ```
   Copia os arquivos `package.json` e `package-lock.json` para o diretório de trabalho no container.

4. **Instalação de Dependências**:
   ```dockerfile
   RUN npm install
   ```
   Instala as dependências definidas no arquivo `package.json`.

5. **Cópia do Código-Fonte**:
   ```dockerfile
   COPY ./src/ .
   ```
   Copia todo o código-fonte da aplicação para o diretório de trabalho no container.

6. **Exposição da Porta**:
   ```dockerfile
   EXPOSE 3000
   ```
   Expõe a porta 3000 para permitir conexões externas à aplicação.

7. **Comando Padrão**:
   ```dockerfile
   CMD ["node", "app.js"]
   ```
   Define o comando padrão para iniciar a aplicação quando o container for executado.

## Como Executar

1. **Construa a Imagem Docker**:
   No diretório onde o arquivo Dockerfile está localizado, execute o seguinte comando para construir a imagem:
   ```bash
   docker build -t custom-nodejs .
   ```

2. **Execute o Container**:
   Após criar a imagem, execute o container com o seguinte comando:
   ```bash
   docker run -d --name nodejs-container -p 3000:3000 custom-nodejs
   ```
   - `-d`: Executa o container em segundo plano.
   - `--name nodejs-container`: Nomeia o container como `nodejs-container`.
   - `-p 3000:3000`: Mapeia a porta 3000 do host para a porta 3000 do container.

3. **Acesse a Aplicação**:
   Após iniciar o container, a aplicação estará disponível em `http://localhost:3000`.

## Observação

Certifique-se de que o arquivo `app.js` seja o ponto de entrada correto da aplicação e que todas as dependências estejam listadas no arquivo `package.json`.
