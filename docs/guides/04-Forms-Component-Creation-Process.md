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

## Render the component in the forms toolbar (Builder Widgets)

These next steps will help you create the Builder Widget, link it to your created component and display it in the forms toolbar.

Lets begin by creating a new folder in the following location: 


``` shell
components/formDesigner/components
```

We'll name the folder "inputComponent" and create a new file within the folder titled "index.tsx".

Lets paste the following code into the newly created index.tsx file.

``` shell
import { IToolboxComponent } from '../../../../interfaces';
import { IConfigurableFormComponent } from '../../../../providers/form/models';
import { BgColorsOutlined } from '@ant-design/icons';
import React from 'react';
import InputComponent, { IInputComponentProps } from '../../../inputComponent';
import _ from 'lodash';

interface IStatisticComponentProps extends IInputComponentProps, IConfigurableFormComponent {}

const ShaInputComponent: IToolboxComponent<IStatisticComponentProps> = {
  type: 'InputComponent',
  name: 'InputComponent',
  icon: <BgColorsOutlined />,
  factory: (model: IStatisticComponentProps) => {
    const {} = model;

    return <InputComponent />;
  },
};

export default ShaInputComponent;

```
Once we have pasted this and saved it, its now time to navigate to the toolboxComponents.ts file which can be located here:


``` shell
src\providers\form\defaults\toolboxComponents.ts
```

Once at the toolboxCOmponent file we'll need to add the following two lines of code, the first line we add the import to the imports section.


``` shell
import InputComponent from '../../../components/formDesigner/components/inputComponent';
```

This next line we add in the 'Basic' area just underneath the last item in the array.


``` shell
InputComponent,
```

Once this is done, we can save all the files and we can navigate to 'TestFormsDesigner' on storybook to see the component added to the Builder Widgets.
