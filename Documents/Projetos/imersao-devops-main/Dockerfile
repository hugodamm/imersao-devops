# Use uma imagem Python oficial e leve como imagem base.
# Alpine é uma boa escolha por seu tamanho reduzido.
FROM python:3.13.5-alpine3.22

# Define o diretório de trabalho dentro do contêiner.
WORKDIR /app

# Copia o arquivo de dependências primeiro para aproveitar o cache do Docker.
# Se o requirements.txt não mudar, esta camada não será reconstruída.
COPY requirements.txt .

# Instala as dependências.
# --no-cache-dir desativa o cache do pip, reduzindo o tamanho da imagem.
RUN pip install --no-cache-dir -r requirements.txt

# Copia o restante do código da aplicação para o diretório de trabalho.
COPY . .

EXPOSE 8000
# Comando para executar a aplicação quando o contêiner iniciar.
# uvicorn é o servidor ASGI recomendado para FastAPI.
# --host 0.0.0.0 torna a aplicação acessível de fora do contêiner.
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
