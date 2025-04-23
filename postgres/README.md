```markdown
# Dockerfile para PostgreSQL

Este arquivo `Dockerfile` é usado para criar uma imagem Docker personalizada para o PostgreSQL. Ele configura um ambiente básico para executar o banco de dados PostgreSQL com credenciais administrativas e um banco de dados inicial.

## Contexto

O PostgreSQL é um banco de dados relacional amplamente utilizado para armazenar dados estruturados. Este `Dockerfile` utiliza a imagem oficial mais recente do PostgreSQL e configura um ambiente inicial com um usuário, senha e banco de dados padrão. Além disso, ele permite a execução de scripts de inicialização opcionais para configurar o banco de dados automaticamente.

## Estrutura do Dockerfile

1. **Imagem Base**:
   ```dockerfile
   FROM postgres:latest
   ```
   Utiliza a imagem oficial mais recente do PostgreSQL como base.

2. **Configuração de Credenciais**:
   ```dockerfile
   ENV POSTGRES_USER=admin
   ENV POSTGRES_PASSWORD=admin_password
   ```
   Define as credenciais administrativas para o PostgreSQL:
   - **Usuário**: `admin`
   - **Senha**: `admin_password`

3. **Banco de Dados Inicial**:
   ```dockerfile
   ENV POSTGRES_DB=satisfaction_survey
   ```
   Define o nome do banco de dados que será criado automaticamente na inicialização.

4. **Exposição da Porta**:
   ```dockerfile
   EXPOSE 5432
   ```
   Expõe a porta padrão do PostgreSQL (5432) para permitir conexões externas.

5. **Scripts de Inicialização (Opcional)**:
   ```dockerfile
   # COPY ./init-scripts/ /docker-entrypoint-initdb.d/
   ```
   Esta linha está comentada, mas pode ser usada para copiar scripts de inicialização para o diretório `/docker-entrypoint-initdb.d/`. Esses scripts serão executados automaticamente quando o container for iniciado.

## Como Executar

1. **Construa a Imagem Docker**:
   No diretório onde o arquivo Dockerfile está localizado, execute o seguinte comando para construir a imagem:
   ```bash
   docker build -t custom-postgres .
   ```

2. **Execute o Container**:
   Após criar a imagem, execute o container com o seguinte comando:
   ```bash
   docker run -d --name postgres-container -p 5432:5432 custom-postgres
   ```
   - `-d`: Executa o container em segundo plano.
   - `--name postgres-container`: Nomeia o container como `postgres-container`.
   - `-p 5432:5432`: Mapeia a porta 5432 do host para a porta 5432 do container.

3. **Conecte-se ao PostgreSQL**:
   Use um cliente PostgreSQL (como `psql` ou uma interface gráfica como o pgAdmin) para se conectar ao banco de dados no endereço `localhost:5432` com as credenciais:
   - **Usuário**: `admin`
   - **Senha**: `admin_password`
   - **Banco de Dados**: `satisfaction_survey`

4. **(Opcional) Scripts de Inicialização**:
   Se você quiser adicionar scripts de inicialização, descomente a linha `COPY` no Dockerfile e coloque seus scripts no diretório `init-scripts`. Recrie a imagem e reinicie o container.

## Observação

Certifique-se de alterar as credenciais padrão (`admin`/`admin_password`) para algo mais seguro em ambientes de produção.
