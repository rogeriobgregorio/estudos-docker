# Usar a imagem oficial do Java como base
FROM openjdk:17-jdk-slim 

# Definir o diretório de trabalho dentro do container
WORKDIR /app

# Copiar o arquivo JAR gerado para o container
COPY target/sua-api.jar app.jar

# Expor a porta onde a API estará escutando
EXPOSE 8080

# Comando para executar a API
CMD ["java", "-jar", "app.jar"]