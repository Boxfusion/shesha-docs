# Quickstart

The starter projects are the best way to get your self started building Shesha apps. You can download the latest core starter project from [Github](https://github.com/Boxfusion/shesha-core-starter)

For this tutorial we will be using docker in ordeer to quickly spin up an SQL Server Instance that we can use for our project but you do not need to use docker.

## Installing SQL Server via Docker

You can find more information about how to install docker and get is started for your platform from the [Docker](https://www.docker.com/get-started) website in our case we will document installing the SQL Servere image and getting the connection string.

Once you have Docker installed you can start a mssql-server instance named "shesha-mssql19" using the latest update for SQL Server 2019

`docker run --name 'shesha-mssql19' -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=yourStrong(!)Password' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest`

In the case above we have setup our sql instance with the database system administrator userid='sa'.

## Restoring the empty database using docker

There is an empty database called *Shesha.bak* in the *db* folder directory of the project that you will need to use to restore the default Shesha Database.

We will demonstrate how to restore the database in docker. 

Once you have created a database and it is up and running you will need to go into the *ShaCompanyName.ShaProjectName.Web.Host > appsettings.json* and change your Default connection string to the connection for the database you created. In our case it will be: `Server=localhost,1433;Database=SheshaDB;User Id=sa;Password=n0-hack.;MultipleActiveResultSets=True`

![appsettings.json screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/appsettings-json-screenshot.png?raw=true)

## Running the Application

In order to run the project you will need to right-click and set the `ShaCompanyName.ShaProjectName.Web.Host` project as the starter project and then click Run.