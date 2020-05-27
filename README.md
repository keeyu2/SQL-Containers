# SQL SERVER AG on Linux Containers
Create SQL AG READSCALE on two containers
1. Create Container sqlserver-bridge
  - sudo docker network create -d bridge --subnet 10.0.0.1/24 sqlserver-bridge
2. create two volumes
-  Sudo docker volume create sql1
-  Sudo docker volume create sql2
3. Pull Docker image
  - docker pull mcr.microsoft.com/mssql/server:2019-latest
3. create two conatiners (replace the port, name, and volume name)
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssword01" \
   -p 1401:1433 --name sql1 --network sqlserver-bridge -v sql1:/var/opt/mssql \
   -d mcr.microsoft.com/mssql/server:2019-latest 
4. Run the Azure Studio Notebook.
