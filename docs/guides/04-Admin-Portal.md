# Admin Portal

## Getting Started

In this tutorial we will introduce you to the Admin Portal app and how to get it set up. 

The main overview page for the Admin Portal app can be found on [Azure](https://dev.azure.com/boxfusion/Shesha-SampleProject). Here you will be able to see the Dev and Test sites for the Sample App.

### Cloning the repository

The first step in cloning the repository is to navigate to the [Azure](https://dev.azure.com/boxfusion/Shesha-SampleProject/_git/SheshaMMSampleAdminPortal) repo and selecting the 'Clone' button on the top right of the page.

![Admin-Portal-Clone screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/Admin-Portal-Clone.PNG?raw=true) 

Once selected you will be presented with numerous ways to clone the repo. 

The easiest method is to select the IDE of your choice and clone it directly in the IDE, this will launch your IDE and prompt you to confirm a clone. 

![admin-portal-select-ide screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/admin-portal-select-ide.PNG?raw=true)

If you prefer to use CLI you can also clone it with the following CLI.

``` shell
https://boxfusion@dev.azure.com/boxfusion/Shesha-SampleProject/_git/SheshaMMSampleAdminPortal
```

Once the repositories are cloned we can continue to the next step.

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
