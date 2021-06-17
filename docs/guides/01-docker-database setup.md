# Docker Database Setup

It is not a requirement to run your application using a docker database but we will go through a quick guide on how to restore the Shesha database to a docker instance.

The instructions below are adapted from the Microsoft documentation for getting started with Microsoft SQL in docker.

## Pull the Container

1. Open a bash terminal on Linux/Mac or an elevated PowerShell session on Windows.
2. Pull the SQL Server 2019 Linux container image from Docker Hub.

=== "Bash"
``` shell
docker pull mcr.microsoft.com/mssql/server:2019-latest
```
=== "Powershell"
``` shell
docker pull mcr.microsoft.com/mssql/server:2019-latest
```

## Run the Container

1. To run the container image with Docker, you can use the following command:

=== "Bash"
``` shell
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   --name 'shesha-mssql19' -p 1401:1433 \
   -v sheshadata:/var/opt/mssql \
   -d mcr.microsoft.com/mssql/server:2019-latest
```
=== "Powershell"
``` shell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   --name "shesha-mssql19" -p 1401:1433 `
   -v sheshadata:/var/opt/mssql `
   -d mcr.microsoft.com/mssql/server:2019-latest
```

!!! note "Host volume mapping notice"
    Host volume mapping for Docker on Windows does not currently support mapping the complete /var/opt/mssql directory. However, you can map a subdirectory, such as /var/opt/mssql/data to your host machine.

    Host volume mapping for Docker on Mac with the SQL Server on Linux image is not supported at this time. Use data volume containers instead. This restriction is specific to the `/var/opt/mssql` directory. Reading from a mounted directory works fine. For example, you can mount a host directory using -v on Mac and restore a backup from a .bak file that resides on the host.

The above command creates a SQL Server 2019 container with the Developer edition (default). SQL Server port 1433 is exposed on the host as port 1401. The optional `-v sheshadata:/var/opt/mssql` parameter creates a data volume container named sheshadata. This is used to persist the data created by SQL Server.

## Change the SA Password

The SA account is a system administrator on the SQL Server instance that's created during setup. After you create your SQL Server container, the `MSSQL_SA_PASSWORD` environment variable you specified is discoverable by running echo `$MSSQL_SA_PASSWORD` in the container. For security purposes, change your SA password:

1. Choose a strong password to use for the SA user.
2. Use docker exec to run the sqlcmd utility to change the password through a Transact-SQL statement. Replace `<YourStrong!Passw0rd>` and `<YourNewStrong!Passw0rd>` with your own password values:

=== "Bash"
``` shell
docker exec -it shesha-mssql19 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourStrong!Passw0rd>' \
   -Q 'ALTER LOGIN SA WITH PASSWORD="<YourNewStrong!Passw0rd>"'
```
=== "Powershell"
``` shell
docker exec -it shesha-mssql19 /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourStrong!Passw0rd>" `
   -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
```

## Create Backup Dierectory

1. First, use docker exec to create a backup folder. The following command creates a `/var/opt/mssql/backup` directory inside the SQL Server container.

=== "Bash"
``` shell
docker exec -it shesha-mssql19 mkdir /var/opt/mssql/backup
```
=== "Powershell"
``` shell
docker exec -it shesha-mssql19 mkdir /var/opt/mssql/backup
```

## Copy Backup to Container

This tutorial uses the empty `Shesha.bak` database backup found on [github](https://github.com/Boxfusion/shesha-core-starter/blob/main/db/Shesha.bak). Use the following steps to backup file into your SQL Server container once you have downloaded it.

Make sure you are running this command in the folder that you downloaded `Shesha.bak` to or you will need to provide the full path to the backup file.

1. Use `docker cp` to copy the backup file into the container in the /var/opt/mssql/backup directory.

=== "Bash"
``` shell
docker cp Shesha.bak shesha-mssql19:/var/opt/mssql/backup
```
=== "Powershell"
``` shell
docker cp Shesha.bak shesha-mssql19:/var/opt/mssql/backup
```

## Confirm Logical File Names

Before restoring the backup, it is important to know the logical file names and file types inside the backup. The following Transact-SQL commands inspect the backup and perform the restore using sqlcmd in the container.

!!! note "Transact-SQL Notice"
    This tutorial uses sqlcmd inside the container, because the container comes with this tool pre-installed. However, you can also run Transact-SQL statements with other client tools outside of the container, such as Visual Studio Code or SQL Server Management Studio. To connect, use the host port that was mapped to port 1433 in the container. In this example, that is localhost,1401 on the host machine and Host_IP_Address,1401 remotely.

1. Run sqlcmd inside the container to list out logical file names and paths inside the backup. This is done with the RESTORE FILELISTONLY Transact-SQL statement.

=== "Bash"
``` shell
docker exec -it shesha-mssql19 /opt/mssql-tools/bin/sqlcmd -S localhost \
   -U SA -P '<YourNewStrong!Passw0rd>' \
   -Q 'RESTORE FILELISTONLY FROM DISK = "/var/opt/mssql/backup/Shesha.bak"' \
   | tr -s ' ' | cut -d ' ' -f 1-2
```
=== "Powershell"
``` shell
docker exec -it shesha-mssql19 /opt/mssql-tools/bin/sqlcmd -S localhost `
   -U SA -P "<YourNewStrong!Passw0rd>" `
   -Q "RESTORE FILELISTONLY FROM DISK = '/var/opt/mssql/backup/Shesha.bak'"
```

You should see output similar to the following:

``` shell
LogicalName PhysicalName
--------------------------
ABPTest e:\Sql2019\Dev\Data\Shesha.mdf
ABPTest_log e:\Sql2019\Dev\Data\ABPTest_log.ldf

(2 rows
```

## Restore Database

Call the RESTORE DATABASE command to restore the database inside the container. Specify new paths for each of the files in the previous step.

=== "Bash"
``` shell
docker exec -it shesha-mssql19 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
   -Q 'RESTORE DATABASE Shesha FROM DISK = "/var/opt/mssql/backup/Shesha.bak" WITH MOVE "ABPTest" TO "/var/opt/mssql/data/Shesha.mdf", MOVE "ABPTest_log" TO "/var/opt/mssql/data/ABPTest_log.ldf"'
```
=== "Powershell"
``` shell
docker exec -it shesha-mssql19 /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
   -Q "RESTORE DATABASE Shesha FROM DISK = '/var/opt/mssql/backup/Shesha.bak' WITH MOVE 'ABPTest' TO '/var/opt/mssql/data/Shesha.mdf', MOVE 'ABPTest_log' TO '/var/opt/mssql/data/ABPTest_log.ldf'"
```

You should see output similar to the following:

``` shell
Processed 1088 pages for database 'Shesha', file 'ABPTest' on file 1.
Processed 2 pages for database 'Shesha', file 'ABPTest_log' on file 1.
RESTORE DATABASE successfully processed 1090 pages in 0.065 seconds (130.949 MB/sec).
```

## Verify Database

1. Run the following query to display a list of database names in your container:

=== "Bash"
``` shell
docker exec -it shesha-mssql19 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
   -Q 'SELECT Name FROM sys.Databases'
```
=== "Powershell"
``` shell
docker exec -it shesha-mssql19 /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
   -Q "SELECT Name FROM sys.Databases"
```

You should see output similar to the following:

``` shell
Name                                                                                                                   
------------
master
tempdb
model 
msdb 
Shesha

(5 rows affected)
```

You are now ready to connect to this database from your app or your favourite Microsoft SQL client. The connection string for your application would look like this:

`Server=localhost,1401;Database=Shesha;User Id=sa;Password=<YourNewStrong!Passw0rd>;MultipleActiveResultSets=True`