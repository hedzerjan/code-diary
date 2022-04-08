# Running SQL Server in Docker
To easily setup and restore databases for a developer, it might be very nice to have the database (or other components) in Docker. MS has a docker image for sql server, it runs on linux.

When this walkthrough is finished you'll have the db running on `localhost,1401`.

## Restoring a backup into a docker container
This [article](https://docs.microsoft.com/en-us/sql/linux/tutorial-restore-backup-in-sql-server-container?view=sql-server-ver15) shows how to create a new container from a MS image for sql server 2019 and how to restore an existing backup into it.

### Howto
Install docker desktop
```bash
sudo docker pull mcr.microsoft.com/mssql/server:2019-latest
```
For M1:
```bash
sudo docker pull mcr.microsoft.com/azure-sql-edge:latest
```
Run the container
```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=YourStrong!Passw0rd' \
   --name 'sql1' -p 1401:1433 \
   -v sql1data:/var/opt/mssql \
   -d mcr.microsoft.com/mssql/server:2019-latest
```
 For M1:
 ```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=YourStrong!Passw0rd' \
   --name 'sql1' -p 1401:1433 \
   -v sql1data:/var/opt/mssql \
   -d mcr.microsoft.com/azure-sql-edge:latest
 ```
make a backup directory in the image:
```bash
sudo docker exec -it sql1 mkdir /var/opt/mssql/backup
```
and copy the backup into the container:
```bash
sudo docker cp WideWorldImporters-Full.bak sql1:/var/opt/mssql/backup
```
restore the database:
```bash
sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost \
   -U SA -P 'YourStrong!Passw0rd' \
   -Q 'RESTORE FILELISTONLY FROM DISK = "/var/opt/mssql/backup/WideWorldImporters-Full.bak"' \
   | tr -s ' ' | cut -d ' ' -f 1-2
```
and next:
```bash
sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P 'YourStrong!Passw0rd' \
   -Q 'RESTORE DATABASE WideWorldImporters FROM DISK = "/var/opt/mssql/backup/WideWorldImporters-Full.bak" WITH MOVE "WWI_Primary" TO "/var/opt/mssql/data/WideWorldImporters.mdf", MOVE "WWI_UserData" TO "/var/opt/mssql/data/WideWorldImporters_userdata.ndf", MOVE "WWI_Log" TO "/var/opt/mssql/data/WideWorldImporters.ldf", MOVE "WWI_InMemory_Data_1" TO "/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1"'
```
# Todo
* [x] Find out how to restore a backup into docker
* [ ] Test restoring an encrypted backup into docker