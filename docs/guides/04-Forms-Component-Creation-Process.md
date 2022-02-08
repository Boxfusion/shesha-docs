# Forms Component Creation Process

## Getting Started

In this tutorial we will introduce you to Forms Component Creation Process and how to get it set up. 

## Creating a Simple Component

Now that we have successfully cloned and run the application and successfully navigated to Storybook its time to create a new simple component.

We will begin by creating a new component within Shesha React JS. Depending on your IDE this can be done in numerous ways, but for the example we will create a component using Microsoft's Visual Studio Code. 

Lets begin by creating a new folder in React JS components which we'll call 'inputComponent'

We'll need to create two new files within the newly created folder. 

=== "index.tsx"
``` shell
title: 'Components/ActionButtonGroup',
```

and

=== "index.stories.tsx"
``` shell
title: 'Components/ActionButtonGroup',
```

![shesha-reactjs-duplicatingComponent screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-duplicatingComponent.PNG?raw=true)

Now lets navigate to the 'index.stories.tsx' file within the newly duplicated component. We will change the title of this component from

=== "Old Title"
``` shell
title: 'Components/ActionButtonGroup',
```
 to 

=== "New Title"
``` shell
title: 'Components/ActionButtonGroupDocumentationTest',
```

lets save the document and you should see the terminal is now recompiling storybook.

![shesha-reactjs-duplicatingComponent-Step2 screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-duplicatingComponent-Step2.PNG?raw=true)

If the terminal does not recompile then its likely that it is not running, to run it you can simply run the following command in your IDE terminal.

``` shell
npm run storybook
```

We can now navigate back to StoryBook which will be running in your browser and look for our newly created component. 

![shesha-reactjs-storybook-creating-component screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-storybook-creating-component.PNG?raw=true)

Congratulations, you have just successfully created a new component with Shesha ReactJS and Storybook! 

## Connecting to APIs

## Creating a Page

## Contributing to the core framework
