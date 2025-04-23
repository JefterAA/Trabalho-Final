# Usa a imagem oficial mais recente do PostgreSQL como base
FROM postgres:latest

# Define o nome de usuário administrativo do banco de dados
ENV POSTGRES_USER=admin

# Define a senha do usuário administrativo
ENV POSTGRES_PASSWORD=admin_password

# Define o nome do banco de dados que será criado automaticamente na inicialização
ENV POSTGRES_DB=satisfaction_survey

# Expõe a porta padrão do PostgreSQL (5432) para permitir conexões externas
EXPOSE 5432

# Opcional: Copia scripts de inicialização para o diretório padrão do PostgreSQL
# Esses scripts serão executados automaticamente quando o container for iniciado
# COPY ./init-scripts/ /docker-entrypoint-initdb.d/