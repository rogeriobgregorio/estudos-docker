# Avançando com Dockerfile

## Comandos Executados:

1. **Criando o arquivo Dockerfile**
   - O Dockerfile define as instruções para criar uma imagem personalizada com mais configurações avançadas.

   **Conteúdo do Dockerfile:**
   ```Dockerfile
   FROM nginx:latest
   # Especifica a imagem base, que é o Nginx na versão mais recente.

   WORKDIR /app
   # Cria o diretório "/app" dentro do contêiner e define-o como diretório de trabalho.

   RUN apt-get update && \
       apt-get install vim -y
   # Atualiza o repositório de pacotes e instala o editor de texto Vim.

   COPY html/ /usr/share/nginx/html
   # Copia os arquivos da pasta local "html/" para o diretório "/usr/share/nginx/html" dentro do contêiner.
   ```

2. **Construindo a imagem a partir do Dockerfile**
   - No terminal, execute o comando para construir a imagem Docker com base no Dockerfile.
   ```bash
   docker build -t rogeriogregorio/nginx-com-vim:latest .
   # Constrói a imagem Docker utilizando o Dockerfile no diretório atual.
   # A imagem será nomeada como "rogeriogregorio/nginx-com-vim:latest".
   ```

3. **Executando o contêiner a partir da imagem criada**
   - Após a construção da imagem, execute o contêiner a partir dessa imagem.
   ```bash
   docker run -it rogeriogregorio/nginx-com-vim:latest bash
   # Executa um contêiner baseado na imagem "rogeriogregorio/nginx-com-vim:latest".
   # O terminal do contêiner será aberto em modo interativo, utilizando o shell bash.
   ```

## Observações:
- O comando `WORKDIR` cria o diretório de trabalho dentro do contêiner e altera o diretório de execução para ele.
- O comando `COPY` permite copiar arquivos ou diretórios do sistema local para dentro do contêiner.
- O uso de `&&` no comando `RUN` permite encadear várias instruções, otimizando o processo de construção da imagem.
