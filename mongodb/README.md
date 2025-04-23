# Dockerfile para MongoDB

Este arquivo `Dockerfile` é usado para criar uma imagem Docker personalizada para o MongoDB. Ele configura um ambiente básico para executar o MongoDB com credenciais administrativas e expõe a porta padrão para conexão.

## Contexto

O MongoDB é um banco de dados NoSQL amplamente utilizado para armazenar dados não estruturados ou semi-estruturados. Este `Dockerfile` utiliza a imagem oficial mais recente do MongoDB e configura um ambiente inicial com um usuário e senha administrativos. Além disso, ele permite a execução de scripts de inicialização opcionais para configurar o banco de dados automaticamente.

## Estrutura do Dockerfile

1. **Imagem Base**:
   ```dockerfile
   FROM mongo:latest
   ```
   Utiliza a imagem oficial mais recente do MongoDB como base.

2. **Configuração de Credenciais**:
   ```dockerfile
   ENV MONGO_INITDB_ROOT_USERNAME=admin
   ENV MONGO_INITDB_ROOT_PASSWORD=adminpassword
   ```
   Define as credenciais administrativas para o MongoDB:
   - **Usuário**: `admin`
   - **Senha**: `adminpassword`

3. **Exposição da Porta**:
   ```dockerfile
   EXPOSE 27017
   ```
   Expõe a porta padrão do MongoDB (27017) para permitir conexões externas.

4. **Scripts de Inicialização (Opcional)**:
   ```dockerfile
   # COPY ./init-scripts /docker-entrypoint-initdb.d/
   ```
   Esta linha está comentada, mas pode ser usada para copiar scripts de inicialização para o diretório `/docker-entrypoint-initdb.d/`. Esses scripts serão executados automaticamente quando o container for iniciado.

## Como Executar

1. **Construa a Imagem Docker**:
   No diretório onde o arquivo Dockerfile está localizado, execute o seguinte comando para construir a imagem:
   ```bash
   docker build -t custom-mongodb .
   ```

2. **Execute o Container**:
   Após criar a imagem, execute o container com o seguinte comando:
   ```bash
   docker run -d --name mongodb-container -p 27017:27017 custom-mongodb
   ```
   - `-d`: Executa o container em segundo plano.
   - `--name mongodb-container`: Nomeia o container como `mongodb-container`.
   - `-p 27017:27017`: Mapeia a porta 27017 do host para a porta 27017 do container.

3. **Conecte-se ao MongoDB**:
   Use um cliente MongoDB (como `mongosh` ou uma interface gráfica como o MongoDB Compass) para se conectar ao MongoDB no endereço `localhost:27017` com as credenciais:
   - **Usuário**: `admin`
   - **Senha**: `adminpassword`

4. **(Opcional) Scripts de Inicialização**:
   Se você quiser adicionar scripts de inicialização, descomente a linha `COPY` no Dockerfile e coloque seus scripts no diretório `init-scripts`. Recrie a imagem e reinicie o container.

## Observação

Certifique-se de alterar as credenciais padrão (`admin`/`adminpassword`) para algo mais seguro em ambientes de produção.
