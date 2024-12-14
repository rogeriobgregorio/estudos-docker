# Iniciando com Bind Mounts

## Comandos Executados:

1. **`docker run -d --name nginx_container -p 8080:80 -v /home/rogerio/projetos/full-cycle/:/usr/share/nginx/html nginx`**
   - Mapeia um diretório local para o diretório `/usr/share/nginx/html` dentro do contêiner, permitindo persistência de arquivos entre o host e o contêiner.

2. **`docker rm nginx_container -f`**
   - Remove o contêiner, mas os arquivos no diretório local permanecem, pois estão fora do contêiner.

3. **Utilizando `--mount` em vez de `-v`:**
   - **`docker run -d --name nginx_container -p 8080:80 --mount type=bind,source="$(pwd)",target=/usr/share/nginx/html nginx`**
     - O comando `--mount` é mais explícito e permite mapear o diretório local para o contêiner.

## Diferença entre `-v` e `--mount`:
- **`-v`**: Se o diretório ou arquivo não existir no host, ele será criado automaticamente.
- **`--mount`**: Retorna erro se o diretório ou arquivo não existir no host.

## Observações:
- Bind mounts são úteis para persistir dados localmente e compartilhar entre o host e o contêiner.