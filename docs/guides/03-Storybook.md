
# Storybook

## Overview

[Storybook](https://storybook.js.org/) is an open source tool for building UI components and pages in isolation. It streamlines UI development, testing, and documentation.

## Getting Started

In this tutorial we will introduce you to Storybook and how to get productive and working within it. 

This guide requires you to have completed the [Shesha React JS Guide](https://shesha-docs.readthedocs.io/en/latest/guides/02-Shesha-ReactJS/) so that you have storybook ready to work with. 

You should be able to view the following page which was run using the following command in Shesha React JS.

``` shell
npm run storybook
```

![Storybook-landing-page screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/Storybook-landing-page.PNG?raw=true)

## Creating Pages for Components

### Storybook Introduction Page

Each component you create on storybook needs to have an introduction page, we use this page to describe what the component is and how we use the component.

![shesha-reactjs-storybook screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/shesha-reactjs-storybook.PNG?raw=true)

This page can be found in the Shesha React JS source code under the following name

``` shell
index.en-US.stories.mdx
```
![storybook-index screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/storybook-index.PNG?raw=true)

When creating new components on Shesha React JS please ensure to create a storybook introduction to the component so that its easy to understand the use cases for each component at a glance. 

### Storybook Component Pages

It's possible to create multiple pages for components in storybook, we use these pages where there are multiple scenario's for components. 

For example if we have a component that has a basic functionality such as a dropdown container displaying a button group we can view the "Basic" page. However if there are scenarios where a component can become quite complex such as a dropdown container with added functionality such as filtering, auto-collapsing or even dynamic data that is displayed we can add as many pages as we need to dive deeper and explain multiple levels of complexity. 

The following image is an example of a component with multiple pages to display different levels of complexity. 

![storybook-multiple-pages screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/storybook-multiple-pages.PNG?raw=true)

As you can see in the above image we have the Collapsible Panel which has a 'Basic' and 'Advanced' page for each.

We can do this by navigating to the following file in the Source code. 

``` shell
index.stories.tsx
```
![storybook-multiple-pages-source screenshot](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/storybook-multiple-pages-source.PNG?raw=true)

As you can see in the above image the Collapsible Panel's 'index.stories.tsx' file has the code which will display the component on Storybook. 


