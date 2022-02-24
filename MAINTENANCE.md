## Building the Docker images

```console
docker build --pull --rm -f "dockerfiles\Dockerfile_0" -t registryhuz5030.azurecr.io/user-java:latest ".\src\user-java"
docker build --pull --rm -f "dockerfiles\Dockerfile_1" -t registryhuz5030.azurecr.io/tripviewer:latest ".\src\tripviewer"
docker build --pull --rm -f "dockerfiles\Dockerfile_2" -t registryhuz5030.azurecr.io/userprofile:latest ".\src\userprofile"
docker build --pull --rm -f "dockerfiles\Dockerfile_3" -t registryhuz5030.azurecr.io/poi:latest ".\src\poi\"
docker build --pull --rm -f "dockerfiles\Dockerfile_4" -t registryhuz5030.azurecr.io/trips:latest ".\src\trips"
```

Push:

```console
docker push registryhuz5030.azurecr.io/poi
docker push registryhuz5030.azurecr.io/user-java
docker push registryhuz5030.azurecr.io/tripviewer
docker push registryhuz5030.azurecr.io/userprofile 
docker push registryhuz5030.azurecr.io/trips
```
AKS CLI Commands

```console

az aks get-credentials --admin --name HackClusterPrivate --resource-group teamResources

az aks update -n HackCluster -g teamResources --attach-acr registryhuz5030


```

Other Commands

```console
docker network create openhack

docker run --network openhack -e ‘ACCEPT_EULA=Y’ -e ‘SA_PASSWORD=Str0ngPa$$w0rd’ --name sql --hostname changeme.database.windows.net -d mcr.microsoft.com/mssql/server:2017-latest


docker exec -it sql "bash"

/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P 'Str0ngPa$$w0rd'

CREATE DATABASE mydrivingDB
SELECT Name from sys.Databases
GO

docker run --network openhack -e SQLFQDN=changeme.database.windows.net -e SQLUSER="sa" -e SQLPASS='Str0ngPa$$w0rd' -e SQLDB=mydrivingDB registryhuz5030.azurecr.io/dataload:1.0

docker run  -p 8080:80 --network openhack --name poi poi

```