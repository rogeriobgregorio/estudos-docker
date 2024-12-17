# Publicando Imagem no DockerHub

## Comandos Executados:

1. **Criando o Dockerfile**
   - O Dockerfile define como a imagem será construída.

   **Conteúdo do Dockerfile:**
   ```Dockerfile
   FROM nginx:latest
   # Especifica a imagem base do Nginx.

   COPY html /usr/share/nginx/html
   # Copia os arquivos da pasta local "html" para o diretório do Nginx no contêiner.

   ENTRYPOINT ["/docker-entrypoint.sh"]
   # Define o script de entrada padrão do contêiner.

   CMD ["nginx", "-g", "daemon off;"]
   # Define o comando padrão para rodar o Nginx no contêiner.
   ```

2. **Construindo e executando a imagem**
   - Execute os seguintes comandos para construir e rodar a imagem:

   ```bash
   docker build -t rogeriogregorio/nginx .
   # Constrói a imagem Docker com o nome "rogeriogregorio/nginx".

   docker run --rm -d -p 8080:80 rogeriogregorio/nginx
   # Executa o contêiner em modo detach (-d), mapeando a porta 8080 do host para a porta 80 do contêiner.
   ```

3. **Criando uma conta no DockerHub**
   - Acesse o [DockerHub](https://hub.docker.com/) e crie uma conta, caso ainda não tenha uma.

4. **Autenticando no DockerHub**
   - No terminal, use o comando para logar no DockerHub:

   ```bash
   docker login
   # Solicita o login no DockerHub para autenticação.
   ```

5. **Publicando a imagem no DockerHub**
   - Depois de logado, use o comando para subir a imagem para o DockerHub:

   ```bash
   docker push rogeriogregorio/nginx
   # Envia a imagem "rogeriogregorio/nginx" para o repositório no DockerHub.
   ```

## Observações:
- O `docker build` cria a imagem com base no Dockerfile, e o `docker run` executa a imagem gerada.
- O `docker push` é utilizado para enviar a imagem local para o repositório no DockerHub, tornando-a disponível publicamente (ou de forma privada, conforme configurações).
- Certifique-se de ter uma conta no DockerHub para realizar o login e o push.
