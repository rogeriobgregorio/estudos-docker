# Trabalhando com Volumes

## Comandos Executados:

1. **`docker volume create meu_volume`**
   - Cria um volume chamado `meu_volume`, que é gerenciado pelo Docker.

2. **`docker volume inspect meu_volume`**
   - Exibe detalhes sobre o volume criado.

3. **`docker run --name nginx_container -d --mount type=volume,source=meu_volume,target=/app nginx`**
   - Monta o volume `meu_volume` no diretório `/app` dentro do contêiner.

4. **`docker volume prune`**
   - Remove volumes não utilizados por contêineres.

5. **`docker volume rm meu_volume`**
   - Remove o volume, desde que não esteja em uso por nenhum contêiner.

## Observações:
- Volumes são úteis para persistir dados de forma independente do ciclo de vida dos contêineres.
- Diferente dos bind mounts, volumes são gerenciados pelo Docker e podem ser compartilhados entre contêineres.
