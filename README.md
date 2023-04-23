Para executar o projeto, siga os seguintes passos:

1. Inicie o WSL (Windows Subsystem for Linux): digite "wsl" no terminal.
2. Inicie o Docker: digite "sudo service docker start" no terminal.
3. Baixe a imagem SDK do .NET 6.0: digite "docker pull mcr.microsoft.com/dotnet/sdk:6.0" no terminal.
4. Entre na raiz do projeto ItemService: digite "cd ItemService" no terminal.
5. Execute o build do container do ItemService: digite "docker build -t itemservice:1.0 ." no terminal.
6. Entre na raiz do projeto RestauranteService: digite "cd RestauranteService" no terminal.
7. Execute o build do container do RestauranteService: digite "docker build -t restauranteservice:1.0 ." no terminal.
8. Crie uma rede de comunicação entre os containers: digite "docker network create --driver bridge restaurante-bridge" no terminal.
9. Crie um container do MySQL: digite "docker run --name=mysql -e MYSQL_ROOT_PASSWORD=root -d --network restaurante-bridge mysql:5.6" no terminal.
10. Rode o container do ItemService: digite "docker run --name=item-service -p 8080:80 --network restaurante-bridge itemservice:1.0" no terminal.
11. Rode o container do RestauranteService: digite "docker run --name=restaurante-service -p 8081:80 --network restaurante-bridge restauranteservice:1.0" no terminal.
12. Com esses passos, o projeto estará rodando em seus containers e você poderá acessá-lo em seu navegador através das URLs "http://localhost:8080" e "http://localhost:8081".