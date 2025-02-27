
# Relatório de Implementação - Docker Compose com Django e Banco de Dados

## Informações Gerais
- **Assunto**: Docker, Containerizar Aplicativos
- **Disciplina**: Sistemas Operacionais
- **Tarefa**: Criar um projeto Django com uma aplicação web, configurar o Docker Compose para rodar o Django e o banco de dados, e realizar a integração entre eles.

## Aluno
- **Nome**: Danilo Ladeira de Oliveira Cosme
- **Matrícula**: 20232014040005

## Relato

### Arquivos Docker e de Configuração do Django

1. **Dockerfile para o Projeto Django**  
   O arquivo `Dockerfile` foi criado com o objetivo de containerizar a aplicação Django. O conteúdo do arquivo é o seguinte:

   **Dockerfile**:
   ```Dockerfile
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
   ```

2. **Arquivo docker-compose.yml**  
   O arquivo `docker-compose.yml` foi configurado para criar dois serviços: um para o aplicativo web Django e outro para o banco de dados. A configuração do arquivo é a seguinte:

   **docker-compose.yml**:
   ```yaml
   version: '3.8'

   services:
     webapp:
       build: .
       command: python manage.py runserver 0.0.0.0:8000
       volumes:
         - .:/app
       ports:
         - "8000:8000"
       depends_on:
         - db
     
     db:
       image: postgres:13
       environment:
         POSTGRES_DB: dbname
         POSTGRES_USER: user
         POSTGRES_PASSWORD: password
       volumes:
         - postgres_data:/var/lib/postgresql/data

   volumes:
     postgres_data:
   ```

3. **Configuração do Django para Acesso ao Banco de Dados Docker**  
   Para que o Django conseguisse se conectar ao banco de dados Postgres rodando no Docker, a configuração do banco no arquivo `settings.py` do Django foi alterada da seguinte forma:

   **settings.py** (trecho relacionado ao banco de dados):
   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': 'dbname',
           'USER': 'user',
           'PASSWORD': 'password',
           'HOST': 'db',
           'PORT': '5432',
       }
   }
   ```

### Testes Realizados

Após a criação dos arquivos e da configuração, o seguinte procedimento foi realizado:

1. **Build da Imagem Docker**  
   A primeira etapa foi a criação da imagem Docker do projeto Django com o comando:

   ```bash
   docker build -t mydjangoapp .
   ```

2. **Subida do Container com Docker Compose**  
   Em seguida, utilizei o comando para subir os containers, o que trouxe tanto o Django quanto o banco de dados Postgres para o ambiente de execução:

   ```bash
   docker-compose up
   ```

   Ao rodar o comando, o serviço Django foi acessado na URL `http://localhost:8000`, confirmando que o container estava funcionando corretamente.

3. **Verificação do Banco de Dados**  
   A integração entre o Django e o banco de dados foi testada criando uma aplicação simples de modelos no Django e verificando se os dados estavam sendo salvos no Postgres.

### Considerações Finais

A tarefa foi realizada com sucesso, e o ambiente foi configurado corretamente usando Docker e Docker Compose. O Dockerfile foi criado para o projeto Django, e o `docker-compose.yml` foi configurado para rodar os dois serviços necessários (Django e banco de dados). Após configurar o arquivo `settings.py` do Django para acessar o banco de dados no Docker, o sistema foi testado e validado.

Todos os arquivos configurados estão disponíveis no repositório fork do projeto.

---

Este é o relatório que foi enviado para o repositório de tarefas.
