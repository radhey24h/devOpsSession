# Introduction 
TODO: This is a project where i have created an angular a react a dotnet core and a node-js application, I have also created a docker images for all the project along with nginx server configuration. 

# Getting Started
TODO: Guide users through getting your code up and running on their own system. In this section you can talk about:
1.	Installation process
2.	Software dependencies
3.	dockerfile and nginx file


# common docker commands
docker build -f Dockerfile -t ang-app . => (go inside project folder and run command to build and tag an image)
docker run -it -p 3000:80 ang-app  => (docker will run the image ang-app in interactive mode on 3000 port )
docker run -D -p 3000:80 ang-app  => (docker will run the image ang-app in dettach mode on 3000 port )
docker ps =>(docker will show containers)
docker ps -a =>(docker will show all the process(container))
docker stop 4bb7ec00c5b4 => (docker will stop the container 4bb7ec00c5b4)
docker rm 4cb626f61e55 => (docker will remove the container 4cb626f61e55)
docker images =>(docker will show all the images)
docker rmi ang-app => (docker will remove a specific image ang-app)
docker system prune  => docker will reomove complete system

# docker sql server local setup
docker pull mcr.microsoft.com/mssql/server:2019-latest   => 
docker exec -it sql_2019_1436 /opt/mssql-tools/bin/sqlcmd -S localhost -U sa  

# docker mongo db local setup
docker run -d --name mongodb -p 27017:27017 mongo   => 
docker exec -it mongodb mongosh 
docker exec -it --name mongodb mongosh 

# docker rabbit mq local setup
docker run --rm -it -p 15672:15672 -p 5672:5672 rabbitmq:3-management  => 

# docker Kafka local setup
docker run --rm -it -p 15672:15672 -p 5672:5672 rabbitmq:3-management  => 