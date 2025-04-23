# Usa a imagem oficial mais recente do MongoDB como base
FROM mongo:latest

# Define variáveis de ambiente para configurar o usuário e senha administrativos do MongoDB
ENV MONGO_INITDB_ROOT_USERNAME=admin
ENV MONGO_INITDB_ROOT_PASSWORD=adminpassword

# Expõe a porta padrão do MongoDB (27017) para permitir conexões externas
EXPOSE 27017

# Copia scripts de inicialização para o diretório padrão do MongoDB (opcional)
# Esses scripts serão executados automaticamente quando o container for iniciado
# COPY ./init-scripts /docker-entrypoint-initdb.d/