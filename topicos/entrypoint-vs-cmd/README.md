# ENTRYPOINT vs CMD

## Comandos Executados:

1. **Usando CMD no Dockerfile**
   - No Dockerfile, o `CMD` define um comando a ser executado quando o contêiner é iniciado.

   **Conteúdo do Dockerfile:**
   ```Dockerfile
   FROM ubuntu:latest
   # Especifica a imagem base, que é o Ubuntu na versão mais recente.

   CMD ["Hello World"]
   # Define o comando a ser executado no contêiner. Neste caso, "Hello World".
   ```

2. **Construindo e executando a imagem com CMD**
   - No terminal, execute o comando para construir e rodar a imagem.
   ```bash
   docker build -t rogeriogregorio/hello .
   # Constrói a imagem Docker utilizando o Dockerfile no diretório atual.
   # A imagem será nomeada como "rogeriogregorio/hello".

   docker run --rm rogeriogregorio/hello
   # Executa o contêiner baseado na imagem "rogeriogregorio/hello" e exibe "Hello World".
   ```

3. **Substituindo o CMD**
   - Ao rodar o contêiner, você pode substituir o comando definido no `CMD`.
   ```bash
   docker run --rm rogeriogregorio/hello echo "oi"
   # Substitui o comando "Hello World" pelo comando "echo 'oi'", exibindo "oi" no terminal.
   ```

---

4. **Usando ENTRYPOINT no Dockerfile**
   - No Dockerfile, o `ENTRYPOINT` define um comando que não pode ser substituído, enquanto o `CMD` pode ser complementado ou substituído.

   **Conteúdo do Dockerfile com ENTRYPOINT:**
   ```Dockerfile
   FROM ubuntu:latest
   # Especifica a imagem base, que é o Ubuntu na versão mais recente.

   ENTRYPOINT ["echo", "Hello"]
   # Define o comando fixo "echo Hello", que não pode ser substituído.

   CMD ["World"]
   # Define um valor padrão para ser passado ao ENTRYPOINT, neste caso, "World".
   ```

5. **Construindo e executando a imagem com ENTRYPOINT**
   - No terminal, execute o comando para construir e rodar a imagem.
   ```bash
   docker build -t rogeriogregorio/hello .
   # Constrói a imagem Docker utilizando o Dockerfile no diretório atual.
   # A imagem será nomeada como "rogeriogregorio/hello".

   docker run --rm rogeriogregorio/hello
   # Executa o contêiner, resultando na saída "Hello World", que é a combinação de ENTRYPOINT e CMD.
   ```

6. **Substituindo o CMD com parâmetros**
   - O `ENTRYPOINT` permanece fixo, enquanto o `CMD` pode ser substituído no comando `docker run`.
   ```bash
   docker run --rm rogeriogregorio/hello Rogerio
   # Executa o contêiner e substitui o valor do CMD por "Rogerio", exibindo "Hello Rogerio".
   ```

## Observações:
- **CMD**: Define o comando a ser executado no contêiner. Pode ser substituído ou complementado durante a execução.
- **ENTRYPOINT**: Define o comando principal a ser executado e não pode ser substituído, mas seu comportamento pode ser alterado com o `CMD`.
- O `CMD` pode ser utilizado para fornecer argumentos padrão ao `ENTRYPOINT`.
