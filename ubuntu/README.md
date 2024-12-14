# 2. Executando o Ubuntu com Docker

## Comandos Executados:

1. **`docker images`**
   - Lista todas as imagens disponíveis localmente.

2. **`docker run -it ubuntu:20.04 bash`**
   - Executa um contêiner da imagem `ubuntu:20.04` e abre um terminal bash interativo, permitindo a interação direta.

3. **`docker run -it --rm ubuntu:20.04 bash`**
   - Semelhante ao comando anterior, mas o contêiner é automaticamente removido após a execução ser interrompida, o que evita acumular contêineres inativos.

## Observações:
- O parâmetro `-it` permite a interação com o terminal dentro do contêiner.
- O comando `--rm` é útil para evitar que o contêiner permaneça após sua execução.