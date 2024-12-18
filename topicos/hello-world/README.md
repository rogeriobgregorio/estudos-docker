# 1. Hello World com Docker

## Comandos Executados:

1. **`docker ps`**
   - Lista todos os containers em execução.

2. **`docker run hello-world`**
   - O comando tenta rodar a imagem `hello-world`. Caso a imagem não esteja localmente, o Docker realiza o *pull* da imagem do Docker Hub.
   - Em seguida, o Docker executa o contêiner e exibe uma mensagem indicando que o Docker foi instalado corretamente.

3. **`docker ps -a`**
   - Lista todos os containers, incluindo os que estão parados.

## Observações:
- O comando `docker run hello-world` serve como uma verificação inicial se o Docker está funcionando corretamente.