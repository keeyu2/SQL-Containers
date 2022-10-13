# SQL SERVER AG on Linux Containers
Introduction
==================================================================================
The goal is to create two containers running SQL Server 2019 and configuring SQL AlwaysOn Availability Group (AAG).  


Directions:
==================================================================================
Install Docker Engine on any supported Linux Distribution or Docker for Mac/windows

1. Create container networking called sqlserver-bridge by runing the command below.  This will allow each container the IP address below instead of the default bridge.
  - sudo docker network create -d bridge --subnet 10.0.0.1/24 sqlserver-bridge

2. Create two container volumes for SQL Server.  This will save the SQL data in each of the volume.
-  Sudo docker volume create sql1
-  Sudo docker volume create sql2

3. Pull Docker image from the Microsoft Docker Hub
  - docker pull mcr.microsoft.com/mssql/server:2019-latest

3. Create two conatiners (replace the port, name, and volume name)
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssword01" \
   -p 1401:1433 --name sql1 --network sqlserver-bridge -v sql1:/var/opt/mssql \
   -d mcr.microsoft.com/mssql/server:2019-latest 

4. Run the Azure Studio Notebook to complete the setup
