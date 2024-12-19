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
# Etapa 1: Construção
FROM maven:3.8.5-openjdk-17-slim AS build

# Definir o diretório de trabalho dentro do container
WORKDIR /app

# Copiar o pom do projeto para dentro do diretório app
COPY pom.xml .

# Baixar as dependências do Maven
RUN mvn dependency:go-offline

# Copiar a pasta src do projeto para a pasta src do container
COPY src /app/src

# Compilar e empacotar o projeto sem a necessidade de executar os testes
RUN mvn clean package -DskipTests

# Etapa 2: Imagem final
FROM openjdk:17-jdk-slim

# Definir o diretório de trabalho dentro do container
WORKDIR /app

# Copiar o arquivo JAR e copiar para o diretório raiz da nova imagem
COPY --from=build /app/target/sua-api.jar app.jar

# Expor a porta onde a API estará escutando
EXPOSE 8080

# Usar ENTRYPOINT para garantir que o comando seja executado com a imagem
ENTRYPOINT ["java", "-jar", "/app/app.jar"]

# Definir o perfil ativo do Spring Boot como "dev"
CMD ["--spring.profiles.active=dev"]
```

**Explicações:**
- `FROM openjdk:17-jdk-slim`: Cria um estágio de construção usando uma imagem base leve do OpendJDK 17 com Maven 3.8.5.
- `WORKDIR /app`: Define um diretório de trabalho dentro do contêiner.
- `COPY --from=build /app/target/sua-api.jar app.jar`: Copia o JAR gerado do projeto para o contêiner.
- `EXPOSE 8080`: Expõe a porta padrão do Spring Boot.
- `CMD`: Define o comando para executar a aplicação.
- `Multistage Build`: A primeira etapa (`build`) compila o projeto usando o Maven e cria o arquivo JAR. A segunda etapa copia apenas o JAR compilado para a imagem final, garantindo uma imagem menor e sem as dependências de build.
- `ENTRYPOINT`: Define o comando para executar o JAR, tornando a imagem mais reutilizável.
- `CMD`: Fornece opções de configuração, como o perfil ativo do Spring (`dev` ou `prod`).

---

## **Passo 3: Construir a Imagem**

Navegue até a pasta do projeto:
   
```bash
cd /caminho/para/o/seu/projeto
```

Execute o comando para construir a imagem com base no Dockerfile:

```bash
docker build -t minha-api-spring:latest .
```

Execute o comando para verificar se a imagem foi construída corretamente:

```bash
docker images
```

**Explicação:**
- `-t minha-api-spring:latest`: Dá um nome e tag para a imagem.
- O ponto (`.`) indica que o Dockerfile está no diretório atual.

---

## **Passo 4: Executar o Contêiner (com volumes ou bind mounts)**

Teste a imagem criando um contêiner:

```bash
docker run -d -p 8080:8080 --name api-spring minha-api-spring:latest
```

Se você precisar de persistência de dados ou quiser usar um bind mount para facilitar o desenvolvimento, pode fazer da seguinte forma:

**Exemplo usando volume para persistência de dados (banco de dados):**

```bash
docker run -d --name meu-banco -v meu_volume:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=senha -e MYSQL_DATABASE=meu_banco -p 3306:3306 mysql:latest
```

**Exemplo usando bind mount para desenvolvimento (por exemplo, mapeando um diretório do host para o contêiner):**

```bash
docker run -d -v /caminho/no/host:/app --name api-spring minha-api-spring:latest
```

**Explicações:**
- `-d`: Executa o contêiner em segundo plano.
- `-p 8080:8080`: Mapeia a porta do host (local) para a porta do contêiner.
- `--name api-spring`: Nomeia o contêiner para facilitar o gerenciamento.
- Volume: Usado para persistir dados no banco de dados. O volume `meu_volume` é mapeado para o diretório do banco de dados dentro do contêiner.
- Bind mount: Permite que você mapeie um diretório do seu sistema de arquivos local para o contêiner, o que é útil durante o desenvolvimento para refletir mudanças instantâneas sem rebuildar a imagem.

---

## **Passo 5: Testar a API**

Abra o navegador ou ferramenta como Postman e acesse `http://localhost:8080` para verificar se a API está funcionando.

---

## **Passo 6: Adicionar Persistência (Se Necessário)**

Caso sua API utilize um banco de dados (como MySQL ou PostgreSQL), você pode:

1. Criar um contêiner para o banco de dados (como mostrado no Passo 4).

2. Configurar a conexão no `application.properties` para apontar para o banco de dados no Docker, como:

   ```properties
   spring.datasource.url=jdbc:mysql://host.docker.internal:3306/meu_banco
   ```

**Explicação**:
- `host.docker.internal`: Usado para acessar o host local a partir de dentro do contêiner.

---

## **Passo 7: Publicar no DockerHub (Opcional)**

Se você deseja compartilhar sua imagem ou usá-la em outro ambiente, pode publicá-la no DockerHub:

1. Faça login no DockerHub:
   ```bash
   docker login
   ```

2. Suba sua imagem para o repositório:
   ```bash
   docker tag minha-api-spring:latest usuario-dockerhub/minha-api-spring:latest
   docker push usuario-dockerhub/minha-api-spring:latest
   ```

**Explicação**:
- A tag `usuario-dockerhub/minha-api-spring:latest` permite que você envie sua imagem para o seu repositório DockerHub.

---

Esse fluxo coloca em prática o aprendizado sobre **imagens**, **contêineres**, **volumes**, **bind mounts**, **ENTRYPOINT**, **CMD**, **multistage builds** e até o **DockerHub**, além de conectar o aprendizado ao mundo real.