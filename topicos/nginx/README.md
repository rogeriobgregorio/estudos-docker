# 3. Publicando Portas com Nginx

## Comandos Executados:

1. **`docker run nginx`**
   - O Docker não encontrou a imagem `nginx` localmente e fez o *pull* da imagem do Docker Hub para executá-la.

2. **`docker run -p 8080:80 nginx`**
   - Mapeia a porta 8080 do localhost para a porta 80 do contêiner, permitindo que a aplicação dentro do contêiner seja acessada na porta 8080 do host.

3. **`docker run -d -p 8080:80 nginx`**
   - Executa o contêiner em modo *detached* (`-d`), ou seja, em segundo plano. Isso permite que o terminal não fique bloqueado pelo processo do contêiner.

## Observações:
- O mapeamento de portas é essencial para expor serviços dentro do contêiner para o host e outros dispositivos na rede.
- O modo *detached* permite continuar utilizando o terminal enquanto o contêiner executa em segundo plano.
