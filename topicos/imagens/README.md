# Entendendo Imagens e DockerHub

## Conceitos:

- **DockerHub**: é o container registry do Docker, onde ficam armazenadas as imagens Docker. Ele funciona como um repositório central para compartilhar e obter imagens.
- **Repositórios de Imagens**: conjunto de imagens relacionadas, onde versões diferentes da mesma imagem podem ser encontradas.
- **Tags**: são marcadores de versão de uma imagem, como `ubuntu:20.04`, permitindo identificar versões específicas.

## Comandos Executados:

1. **`docker pull ubuntu`**
   - Baixa a imagem `ubuntu` do DockerHub para o repositório local.

2. **`docker images`**
   - Lista todas as imagens disponíveis localmente no seu sistema Docker.

3. **`docker rmi ubuntu`**
   - Remove a imagem `ubuntu` do repositório local.

## Observações:
- As imagens podem ser armazenadas localmente e compartilhadas através do DockerHub.
- O comando `docker rmi` é usado para remover imagens locais que não estão mais em uso.