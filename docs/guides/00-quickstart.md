# Quickstart Guide

This quickstart guide will help you get setup with Shesha. The starter projects are the best way to get your self started building Shesha apps.

## Components

The Shesha quickstart consists of 4 main components.

- **Database:** A clean sample database that contains all the default tables and migrations needed to seed a new database and application.
- **Backend:** A sample backend application with APIs and services that allow you to interacte with a Shesha application from a totally decoupled system. The admin and public portals depend on this backend.
- **Admin Portal:** A sample admin portal that contains default functionailty for administratiing a shesha application. These includes functionality to administer roles and permissions, create new forms, etc.
- **Public Portal:** A sample public portal app which is totally decoupled from the admin portal and provides a demo on how you can consume the APIs and services from a third party app. The public portal app also leverages the components provided by Shesha to show you how you can use these when building your application.

Below is a diagram that shows how these applications can be typically deployed in a real world situation.

![components diagram](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/components.png?raw=true)

## Downloading The Artificats

This step will show you how you can download all the repositories you'll need to get Shesha up and running. You can click the following link in order to download the required artifacts.

[Download SheshaArtifacts.zip](https://github.com/Boxfusion/shesha-docs/blob/e9e08dffa636792399f740c141b402c60c11b839/docs/assets/SheshaArtifacts.zip)

![download link](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-artifacts-download-link.png?raw=true)

The link should include the following files or folders:

- Shesha.bak (Database)
- SheshaMMSampleAdminPortal (Admin Portal)
- SheshaMMSampleBackend (Backend)
- SheshaMMSamplePublicPortal (Public Portall)

## Requirements

Before you can get start you will need to make sure that you have the following development tools installed on your machine.

- **Database:** Microsoft SQL Server Management Studio v18.10, Microsoft SQL Server 2019
- **Backend:** Microsoft Visual Studio, .NET Core
- **Admin and Public Portals:** NodeJS, Python, Sass

## Setting Up The Database

Once you have downloaded the artifacts you can start by restoring the provided database that your portal apps can connect to. In this instance we are going to be using Microsoft SQL Server Management Studio v18.10.

This guide will not be showing you how to install Microsoft SQL Server Management Studio v18.10 or how to create a server instance that you can connect to as it is beyond the scope of this tutorial.

- Open up Microsoft SQL Server Management Studio and Connect to a Server 

![step 1: setting up the database](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/setting-up-the-database-1.png?raw=true)

- Right click the "Databases" node and select "Restore Database" 

![step 2: setting up the database](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/setting-up-the-database-2.png?raw=true)

- Select "Device" from your source tabe and locate the "Shesha.bak" file by clicking the "Add" button. You might need to place the backup direcly on your C drive if you are having issues locating it due to permissions. 

![step 3: setting up the database](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/setting-up-the-database-3.png?raw=true)

- Once you have added the backup you can click "Verify Backup Media" and once all is set you can click the "OK" button to complete the import 

![step 4: setting up the database](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/setting-up-the-database-4.png?raw=true)

## Setting Up The Backend

## Setting Up The Admin Portal

### Getting Started

In this tutorial we will introduce you to the Admin Portal app and how to get it set up. 

### Run the app

Once you have cloned and opened the repo its now time to get any missing dependencies and run the app. 

The first step is to run the following CLI in your chosen IDE and update all the node packages. 

``` shell
npm i
```

![admin-portal-cli-npm screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/admin-portal-cli-npm.PNG?raw=true)

Running this CLI will update and get any node packages you will need to run the Admin Portal app.

![admin-portal-cli-npm-packages screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/admin-portal-cli-npm-packages.PNG?raw=true)

Once this step is complete we can now run the app using the following CLI

``` shell
npm run dev
```

This will then build and serve the application on the following URL

``` shell
http://localhost:3050
```

You can manually navigate there or (ctrl + click) on the URL when it appears in your IDE teerminal. This will launch the following screen.

![admin-portal-welcome-screen screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/admin-portal-welcome-screen.PNG?raw=true)

We can now log in using the following username and password.

=== "Username"
``` shell
admin
```
=== "Password"
``` shell
123qwe
```

Congratulations, you have now succeessfully cloned and run the Shesha Admin Portal app!

## Setting Up The Public App
