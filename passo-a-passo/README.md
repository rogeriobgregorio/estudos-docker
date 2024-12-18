# Passo a passo: dockerizando um projeto.

Este passo a passo integra os aprendizados vistos até o momento e mostra como aplicar o Docker de forma prática em um projeto Java Spring.

---

## **Passo 1: Preparar o Ambiente do Projeto**

1. Certifique-se de que a API REST está funcionando localmente.
2. Confirme que o projeto tem um **arquivo JAR** gerado após a compilação (usando `mvn package` ou similar).

---

## **Passo 2: Criar um Dockerfile**

O Dockerfile é o ponto central para criar a imagem. Um exemplo para uma API REST seria:

```Dockerfile
# Usar a imagem oficial do Java como base
FROM openjdk:17-jdk-slim 

# Definir o diretório de trabalho dentro do container
WORKDIR /app

# Copiar o arquivo JAR gerado para o container
COPY target/sua-api.jar app.jar

# Expor a porta onde a API estará escutando
EXPOSE 8080

# Comando para executar a API
CMD ["java", "-jar", "app.jar"]
```

**Explicações:**
- `FROM openjdk:17-jdk-slim`: Usa uma imagem base leve do Java 17.
- `WORKDIR /app`: Define um diretório de trabalho dentro do contêiner.
- `COPY target/sua-api.jar app.jar`: Copia o JAR gerado do projeto para o contêiner.
- `EXPOSE 8080`: Expõe a porta padrão do Spring Boot.
- `CMD`: Define o comando para executar a aplicação.

---

## **Passo 3: Construir a Imagem**

Navegue até a pasta do projeto:
   
```bash
cd /caminho/para/o/seu/projeto
```

Use o comando para criar a imagem com base no Dockerfile:

```bash
docker build -t minha-api-spring:latest .
```

**Explicação:**
- `-t minha-api-spring:latest`: Dá um nome e tag para a imagem.
- O ponto (`.`) indica que o Dockerfile está no diretório atual.

---

## **Passo 4: Executar o Contêiner**

Teste a imagem criando um contêiner:

```bash
docker run -d -p 8080:8080 --name api-spring minha-api-spring:latest
```

**Explicações:**
- `-d`: Executa o contêiner em segundo plano.
- `-p 8080:8080`: Mapeia a porta do host (local) para a porta do contêiner.
- `--name api-spring`: Nomeia o contêiner para facilitar o gerenciamento.

---

## **Passo 5: Testar a API**

Abra o navegador ou ferramenta como Postman e acesse `http://localhost:8080` para verificar se a API está funcionando.

---

## **Passo 6: Adicionar Persistência (Se Necessário)**

Caso sua API utilize um banco de dados (como MySQL ou PostgreSQL), você pode:
1. Criar um contêiner para o banco de dados:
   ```bash
   docker run -d --name meu-banco -e MYSQL_ROOT_PASSWORD=senha -e MYSQL_DATABASE=meu_banco -p 3306:3306 mysql:latest
   ```
2. Configurar a conexão no `application.properties` para apontar para o banco no Docker (`jdbc:mysql://host.docker.internal:3306/meu_banco`).

---

## **Passo 7: Publicar no DockerHub (Opcional)**

1. Faça login no DockerHub:
   ```bash
   docker login
   ```
2. Suba sua imagem para o repositório:
   ```bash
   docker tag minha-api-spring:latest usuario-dockerhub/minha-api-spring:latest
   docker push usuario-dockerhub/minha-api-spring:latest
   ```

---

Esse fluxo coloca em prática o aprendizado sobre imagens, contêineres, volumes, e até o DockerHub, além de conectar o aprendizado ao mundo real.