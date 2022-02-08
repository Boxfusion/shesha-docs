# Forms Component Creation Process

## Getting Started

In this tutorial we will introduce you to Forms Component Creation Process and how to get it set up. 

## Creating a Simple Component

Now that we have successfully cloned and run the application and successfully navigated to Storybook its time to create a new simple component.

We will begin by creating a new component within Shesha React JS. Depending on your IDE this can be done in numerous ways, but for the example we will create a component using Microsoft's Visual Studio Code. 

Lets begin by creating a new folder in React JS components which we'll call 'inputComponent'

We'll need to create two new files within the newly created folder. 

``` shell
index.tsx,
```


and


``` shell
index.stories.tsx,
```


Now lets navigate to the 'index.tsx' file within the newly created component. We will add the following code to the file:


``` shell
import React, { FC } from 'react';
import { Input } from 'antd';

export interface IInputComponentProps {}

/**
A Basic Input Component for Documentation
 */

export const InputComponent: FC<IInputComponentProps> = ({}) => {
  return <Input placeholder="Basic usage" />;
};

export default InputComponent;
```

Once that is done we will add the following code to the 'index.stories.tsx' file: 

``` shell
import React from 'react';
import { Meta } from '@storybook/react/types-6-0';
import { Story } from '@storybook/react';
import InputComponent, { IInputComponentProps } from '.';

export default {
  title: 'Components/TestInputComponent',
  component: InputComponent,
  argTypes: {},
} as Meta;

// Create a master template for mapping args to render the Input component
const Template: Story<IInputComponentProps> = args => <InputComponent {...args} />;

// Reuse that template for creating different stories
export const Basic = Template.bind({});
Basic.args = {};
```


Now Lets save both files and run the following command:


``` shell
npm run storybook
```


We can now navigate to Storybook and see the following component has successfully been created and is being displayed within Storybook. 

