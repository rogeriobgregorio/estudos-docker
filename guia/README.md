# Docker: Guia de Aprendizado

Este README tem como objetivo detalhar o processo de aprendizado sobre o **Docker**, cobrindo desde os conceitos fundamentais até os comandos e práticas essenciais no uso dessa plataforma para criação e gerenciamento de containers.

---

## 1. O que é Docker?
Docker é uma plataforma de código aberto que permite desenvolver, empacotar e executar aplicações em **containers**. Ele isola a aplicação em um ambiente controlado, garantindo que ela seja executada de forma consistente, independentemente de onde o container esteja sendo executado (em servidores locais, na nuvem, etc.).

---

## 2. O que são containers?
Containers são unidades isoladas que empacotam o código de uma aplicação e todas as suas dependências (como bibliotecas e configurações), garantindo que a aplicação possa ser executada em qualquer ambiente sem conflitos. Diferentemente das máquinas virtuais, os containers não emulam um sistema operacional completo, o que torna seu uso mais eficiente em termos de recursos.

---

## 3. O que é namespace?
**Namespaces** são uma funcionalidade do kernel Linux que permite o isolamento de recursos, como processos, redes e sistemas de arquivos. No contexto do Docker, cada container opera em seu próprio namespace, o que significa que ele tem acesso a seus próprios recursos, sem interferir nos recursos do sistema host ou de outros containers.

---

## 4. O que é cgroup?
**Control groups (cgroups)** são um recurso do kernel Linux utilizado para gerenciar o uso de recursos, como CPU, memória e disco, por processos. No Docker, cgroups limitam o uso de recursos de cada container, garantindo que ele não consuma mais do que os recursos alocados para ele.

---

## 5. O que é union file system?
O **Union File System (UFS)** é uma técnica que combina várias camadas de sistemas de arquivos em uma única visão. No Docker, ele permite a criação de imagens de containers em camadas, onde cada alteração ou atualização em um container é registrada como uma nova camada. Isso torna as imagens mais eficientes em termos de armazenamento e acelera o processo de criação de containers.

---

## 6. O que é Dockerfile?
Um **Dockerfile** é um arquivo de texto que contém uma lista de instruções para a criação de uma imagem Docker. Ele define qual imagem base será utilizada, quais dependências serão instaladas, quais arquivos serão copiados para o container e outros aspectos essenciais para a construção de um container configurado corretamente.

---

## 7. O que é imagem?
Uma **imagem Docker** é um pacote imutável que contém todos os arquivos e configurações necessários para executar uma aplicação. Ela serve como a base para a criação de containers, proporcionando um ambiente consistente para a execução de software.

---

## 8. O que é image registry?
Um **Image Registry** é um repositório onde as imagens Docker são armazenadas e distribuídas. O Docker Hub é o registry público mais popular, mas é possível usar outros, como o **AWS ECR** (Elastic Container Registry) ou o **GitHub Container Registry**. Essas imagens podem ser baixadas, compartilhadas e versionadas conforme necessário.

---

## 9. Diferença entre container e máquina virtual
- **Container**: Compartilha o kernel do sistema host, o que o torna mais leve e rápido para inicializar, além de consumir menos recursos.
- **Máquina Virtual**: Emula todo o hardware, incluindo o kernel, o que resulta em maior consumo de recursos e tempos de inicialização mais longos.

---

## 10. O que é overlay file system?
O **OverlayFS** é um tipo de sistema de arquivos utilizado pelo Docker para combinar múltiplas camadas de sistemas de arquivos. Ele permite que as modificações feitas em um container sejam armazenadas separadamente, sem modificar as camadas de base da imagem Docker.

---

## 11. O que é daemon - API?
- **Daemon**: O processo principal do Docker que executa e gerencia containers, imagens, volumes e redes. Ele roda em segundo plano e é responsável por todas as interações com a plataforma.
- **API**: A interface de programação que permite que ferramentas externas (como o Docker CLI ou outras interfaces) se comuniquem com o daemon Docker para gerenciar containers e imagens.

---

## 12. O que são volumes?
**Volumes** são mecanismos de persistência de dados em Docker. Diferente dos dados armazenados dentro de um container, que são efêmeros, os volumes permanecem disponíveis mesmo após a remoção do container. Eles são úteis para armazenar dados que precisam ser mantidos, como bancos de dados ou arquivos de configuração.

---

## 13. Como funciona o Docker?
O Docker utiliza **containers** para isolar aplicações e suas dependências. Ao criar um container, o Docker utiliza a imagem especificada, configurando o ambiente conforme as instruções contidas no **Dockerfile**. O daemon Docker gerencia o ciclo de vida dos containers e utiliza **namespaces** para garantir o isolamento e **cgroups** para limitar o uso de recursos.

---

## 14. Fluxo para containizar uma aplicação com Docker
1. **Preparar o ambiente**: Certifique-se de que o código e as dependências estão prontos.
2. **Criar um Dockerfile**: Defina a imagem base e os pacotes que precisam ser instalados.
3. **Construir a imagem**: Utilize o comando `docker build` para criar a imagem a partir do Dockerfile.
4. **Executar o container**: Use `docker run` para iniciar um container a partir da imagem.
5. **Configurar volumes e redes**: Mapeie diretórios para persistir dados e configure redes, se necessário.
6. **Testar e ajustar**: Verifique se o container está funcionando corretamente e faça ajustes.
7. **Publicar a imagem**: Envie a imagem para um repositório para compartilhamento ou implantação.

---

## 15. O que é Docker Compose?
O **Docker Compose** é uma ferramenta para definir e executar aplicações multi-containers. Utilizando um arquivo YAML (`docker-compose.yml`), é possível configurar todos os containers, redes e volumes necessários para uma aplicação, facilitando a orquestração e a gestão de dependências entre eles.

---

## 16. O que faz o comando `build`?
O comando **`docker build`** cria uma imagem Docker a partir de um **Dockerfile**. Ele processa as instruções definidas no Dockerfile e gera a imagem que pode ser utilizada para criar containers.

Exemplo:
```bash
docker build -t minha-imagem .
```
- `-t`: Especifica o nome da imagem.
- `.`: O contexto é o diretório atual.

---

## 17. O que faz o comando `run`?
O comando **`docker run`** é usado para criar e iniciar um container a partir de uma imagem Docker. Ele pode incluir várias opções para configurar o container, como mapeamento de portas e volumes.

Exemplo:
```bash
docker run -d -p 8080:80 minha-imagem
```
- `-d`: Executa o container em segundo plano.
- `-p`: Mapeia a porta 8080 do host para a porta 80 do container.

---

## 18. Quais os principais e mais usados comandos?
Aqui estão alguns dos comandos mais importantes e usados no Docker:

- **`docker build`**: Cria uma imagem a partir de um Dockerfile.
- **`docker run`**: Cria e executa um container a partir de uma imagem.
- **`docker ps`**: Lista os containers em execução.
- **`docker ps -a`**: Lista todos os containers, incluindo os parados.
- **`docker images`**: Lista todas as imagens disponíveis localmente.
- **`docker pull`**: Baixa uma imagem de um repositório.
- **`docker push`**: Envia uma imagem para um repositório.
- **`docker stop`**: Para um container em execução.
- **`docker rm`**: Remove um container.
- **`docker rmi`**: Remove uma imagem.
- **`docker logs`**: Exibe os logs de um container.
- **`docker exec`**: Executa comandos dentro de um container.
- **`docker-compose up`**: Inicia os containers definidos no arquivo `docker-compose.yml`.
- **`docker-compose down`**: Encerra e remove os containers do Compose.
