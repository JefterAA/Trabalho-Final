FROM MongoDB

# Diretório de trabalho dentro do contêiner
WORKDIR /app

# Copiar os arquivos necessários para o contêiner
COPY requirements.txt ./
COPY . .

# Instalar as dependências
RUN pip install --no-cache-dir -r requirements.txt

# Expor a porta padrão do Streamlit
EXPOSE 2424

# Comando para iniciar o aplicativo Streamlit
CMD ["streamlit", "run", "faq_app.py", "--server.port=8501", "--server.address=0.0.0.0"]