# Shesha React JS

## Getting Started

In this tutorial we will introduce you to Shesha React JS and how to get it set up. 

### Cloning the repository

The first step in cloning the repository is to navigate to the Shesha [Github](https://github.com/Boxfusion/shesha-reactjs) repo and selecting the green 'Code' button on the top right of the center page.

![shesha-reactjs-clone screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-clone.PNG?raw=true) 

Once selected you will be presented with numerous ways to clone the repo, most notably HTTPS, SSH and GitHub CLI. 

The easiest method is to select 'Open with GitHub Desktop' which will launch the following screen.

![shesha-reactjs-github screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-github.PNG?raw=true)

This screen allows you to save it to the directory of your choice, just confirm it and no other settings need to be changed.

If you do not already have GitHub Desktop you can download it from [Github's Official Website](https://desktop.github.com/)

Once it is downloaded we can proceed to opening the folder in your choice of IDE.

### Run the app

Once you have cloned and opened the repo its now time to get any missing dependencies and run the app. 

The first step is to run the following CLI in your chosen IDE and update all the node packages. 

``` shell
npm i
```

![shesha-reactjs-npm screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-npm.PNG?raw=true)

Running this CLI will update and get any node packages you will need to run the Admin Portal app. This step may take a while depending on your internet speed.

![shesha-reactjs-node screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-node.PNG?raw=true)

Once this step is complete we can now run the app using the following CLI

``` shell
npm run storybook
```

This will then build and serve storybook on the following URL's

=== "Local"
``` shell
http://localhost:6006/
```
=== "On your network"
``` shell
http://192.168.0.104:6006/
```

You can manually navigate there or (ctrl + click) on the URL when it appears in your IDE teerminal. This will launch the following screen.

![shesha-reactjs-storybook screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-storybook.PNG?raw=true)


## Creating a Component

Now that we have successfully cloned and run the application and successfully navigated to Storybook its time to create a new simple component.

We will begin by creating a new component within Shesha React JS. Depending on your IDE this can be done in numerous ways, but for the example we will create a component using Microsoft's Visual Studio Code. 

Lets begin by duplicating a simplpe component such as the 'actionButtonGroup'

## Connecting to APIs

## Creating a Page

## Contributing to the core framework
