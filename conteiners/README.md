# Removendo Containers

## Comandos Executados:

1. **`docker rm 73dafed40e5a`**
   - Remove um contêiner específico pelo ID.

2. **`docker rm hungry_shirley`**
   - Remove um contêiner pelo nome.

3. **`docker rm f1723a98acb3 -f`**
   - Força a remoção de um contêiner que está em execução.

4. **`docker rm $(docker ps -a -q)`**
   - Remove todos os containers, utilizando o comando `docker ps -a -q` para listar apenas os IDs dos contêineres.

## Observações:
- O comando `docker rm` é utilizado para remover contêineres.
- O parâmetro `-f` força a remoção de contêineres em execução.