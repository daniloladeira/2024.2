 # Imagem base do Python
 FROM python:3.10-slim

 # Definir diretório de trabalho
 WORKDIR /app

 # Copiar arquivos de dependências
 COPY requirements.txt /app/

 # Instalar dependências
 RUN pip install --no-cache-dir -r requirements.txt

 # Copiar o código da aplicação
 COPY . /app/

 # Expor a porta em que a aplicação irá rodar
 EXPOSE 8000

 # Comando para rodar o Django
 CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]