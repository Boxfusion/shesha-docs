# Quickstart

The starter projects are the best way to get your self started building Shesha apps. You can download the latest core starter project from [Github](https://github.com/Boxfusion/shesha-core-starter)

For this tutorial we will be using docker in ordeer to quickly spin up an SQL Server Instance that we can use for our project but you do not need to use docker.

## Installing SQL Server via Docker

You can find more information about how to install docker and get is started for your platform from the [Docker](https://www.docker.com/get-started) website in our case we will document installing the SQL Servere image and getting the connection string.

Once you have Docker installed you can start a mssql-server instance using the latest update for SQL Server 2017

`docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=yourStrong(!)Password' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2017-latest`

In the case above we have setup our sql instance with the database system administrator userid='sa'.

Make sure you create a database that you will use, in this case we have created a database called `SheshaDB`

The connection string will be:

`Server=localhost,1433;Database=Shesha;User Id=sa;Password=n0-hack.;MultipleActiveResultSets=True`

The steps for creating the database are beyond the scope of this tutorial.