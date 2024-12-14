# Acessando e Alterando Arquivos de um Contêiner

## Comandos Executados:

1. **`docker run -d --name nginx_container -p 8080:80 nginx`**
   - Executa o contêiner `nginx` em segundo plano, nomeando-o como `nginx_container` e mapeando a porta 8080 do host para a porta 80 do contêiner.

2. **`docker exec nginx_container ls`**
   - Executa o comando `ls` dentro do contêiner, listando os arquivos.

3. **`docker exec nginx_container bash`**
   - Executa o comando `bash` dentro do contêiner, permitindo acesso à linha de comando.

4. **`docker exec -it nginx_container bash`**
   - Abre um terminal interativo dentro do contêiner.

5. **Interação com arquivos no contêiner:**
   - **`cd /usr/share/nginx/html/`**: Navega até o diretório de arquivos HTML do Nginx.
   - **`apt-get update`**: Atualiza o sistema Ubuntu dentro do contêiner.
   - **`apt-get install vim`**: Instala o editor de texto Vim.
   - **`vim index.html`**: Edita o arquivo `index.html` dentro do contêiner.
   - **Comandos do Vim:**
     - "i" entra no modo de edição.
     - "esc" sai do modo de edição.
     - ":w" salva as alterações.
     - ":q" sai do Vim.
     - ":wq" salva e sai do Vim.
     - ":q!" sai sem salvar.
     - `ctrl+d` encerra o shell.

## Observações:
- Modificações feitas dentro do contêiner não são persistentes após sua remoção, a menos que você use volumes ou bind mounts.