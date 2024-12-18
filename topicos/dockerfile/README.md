# Criando a Primeira Imagem com Dockerfile

## Comandos Executados:

1. **Criando o arquivo Dockerfile**
   - O Dockerfile define as instruções para criar uma imagem personalizada.

   **Conteúdo do Dockerfile:**
   ```Dockerfile
   FROM nginx:latest
   # Especifica a imagem base, que é o Nginx na versão mais recente.

   RUN apt-get update
   RUN apt-get install vim -y
   # Atualiza o repositório de pacotes e instala o editor de texto Vim.
   ```

2. **Construindo a imagem a partir do Dockerfile**
   - No terminal, execute o comando para construir a imagem Docker baseada no Dockerfile.
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
- O comando `docker build` cria uma imagem a partir de um Dockerfile, permitindo personalizar a configuração do contêiner.
- O parâmetro `-t` no comando `docker build` é utilizado para nomear a imagem.
- O comando `docker run -it` permite iniciar o contêiner e interagir com ele diretamente através do terminal.