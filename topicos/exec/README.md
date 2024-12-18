# Docker ENTRYPOINT exec

## Comandos Executados:

1. **Visualizando ENTRYPOINT e CMD de uma Imagem**
   - Para visualizar o `ENTRYPOINT` e o `CMD` de uma imagem, você pode acessar a versão da imagem no Docker Hub e consultar o repositório no GitHub onde o arquivo Dockerfile da imagem está hospedado.

2. **Executando um Contêiner com Bash**
   - No terminal, execute o comando para rodar um contêiner da imagem `nginx` com o comando `bash`, substituindo o `CMD` da imagem.
   ```bash
   docker run --rm nginx bash
   # Executa um contêiner baseado na imagem "nginx".
   # O comando "bash" substitui o CMD da imagem, iniciando o shell bash no contêiner.
   ```

3. **Uso do comando exec "$@"**
   - O comando `exec "$@"` dentro do Dockerfile permite que o contêiner execute qualquer comando passado como argumento, substituindo o processo em execução com o novo comando.

## Observações:
- O comando `docker run --rm` executa o contêiner e o remove automaticamente após sua execução.
- O uso de `exec "$@"` permite que o contêiner aceite parâmetros dinâmicos para substituir o processo principal, proporcionando flexibilidade ao executar comandos no contêiner.
