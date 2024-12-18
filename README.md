# Estudos Docker

Este repositório contém as anotações e práticas realizadas durante o meu estudo de **Docker**. Aqui, documentei os principais conceitos, comandos e exemplos que explorei para entender e aplicar as funcionalidades dessa plataforma de containers.

## Comece aqui
**[Introdução](guia/README.md)**

## Índice
1. **[Hello World com Docker](topicos/hello-world/README.md)**  
   Um primeiro contato com o Docker, criando e executando um container simples para entender o funcionamento básico.

2. **[Executando o Ubuntu com Docker](topicos/ubuntu/README.md)**  
   Como criar e rodar um container baseado na imagem do Ubuntu, explorando a interação com o sistema operacional dentro do container.

3. **[Publicando Portas com Nginx](topicos/nginx/README.md)**  
   Exemplificando como publicar portas para acesso externo, utilizando o servidor web Nginx em um container Docker.

4. **[Removendo Contêineres](topicos/conteiners/README.md)**  
   Como remover containers que não são mais necessários, garantindo uma gestão eficiente dos recursos.

5. **[Acessando e Alterando Arquivos de um Contêiner](topicos/arquivos/README.md)**  
   Mostra como acessar e modificar arquivos dentro de um container em execução, explorando a interatividade e gestão de dados.

6. **[Bind Mounts](topicos/bind-mounts/README.md)**  
   Explicação e demonstração do uso de bind mounts para mapear arquivos e diretórios entre o host e o container.

7. **[Trabalhando com Volumes](topicos/volumes/README.md)**  
   Como criar e utilizar volumes Docker para persistir dados de maneira eficiente, independente do ciclo de vida dos containers.

8. **[Entendendo imagens e DockerHub](topicos/imagens/README.md)**  
   Explicação sobre o DockerHub, como baixar, listar e remover imagens, e o uso de tags para versões específicas.

9. **[Criando a primeira imagem com Dockerfile](topicos/dockerfile/README.md)**  
   Instruções para criar uma imagem personalizada com Dockerfile, incluindo a instalação do Vim em um contêiner Nginx.

10. **[Avançando com Dockerfile](topicos/dockerfile-avancado/README.md)**  
   Criando uma imagem Docker personalizada com diretório de trabalho, instalação de pacotes e cópia de arquivos.

11. **[ENTRYPOINT vs CMD](topicos/entrypoint-vs-cmd/README.md)**  
   Diferença entre ENTRYPOINT e CMD no Dockerfile, mostrando como cada um define o comportamento de execução de comandos no contêiner.

12. **[Docker ENTRYPOINT exec](topicos/exec/README.md)**  
   Como visualizar e substituir o ENTRYPOINT e CMD de uma imagem, usando exec "$@" e o shell bash.

13. **[Publicando imagem no DockerHub](topicos/dockerhub-publicacao/README.md)**  
   Como criar, construir e enviar uma imagem para o DockerHub.

14. **[Passo a passo: dockerizando um projeto](passo-a-passo/README.md)**  
   Colocando em prática todo o aprendizado visto até aqui em uma aplicação real.

## Material de Apoio
- **[Roadmap Docker](roadmap/docker-roadmap.pdf)**
- **[Descomplicando o Docker](https://livro.descomplicandodocker.com.br/)**
- **[Contêineres com Docker do Desenvolvimento à Produção](https://github.com/free-educa/books/blob/main/books/Containers%20com%20Docker%20do%20Desenvolvimento%20a%20Producao.pdf)**