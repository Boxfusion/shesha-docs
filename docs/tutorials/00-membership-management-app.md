# Membership Management App

For this introduction we will be building a membership management app which is designed for organisations that want to manage memberships such as political parties and schools. The tutorial is designed to teach you the basics of how building a Shesha based application works. Each step is designed to introduce you to some of the key concepts within Shesha.

NB: You will need to make sure that you have completed the [Quickstart Guide](https://shesha-docs.readthedocs.io/en/latest/guides/00-quickstart/) guide on how to get setup.

In this tutorial, you learn how to:

- Configure user roles
- Configure menus
- Configure, create and edit custom forms
- Creating and managing reference lists
- Adding a model class and database migrations
- Creating a API service
- Calling the API service from Postman
- Capturing data using our form from the admin portal
- Capturing data from a custom form the public portal

At the end of this tutorial you will have a membership management app this will allow you to capture new membership details using your designed forms and saving them in your database.

## Getting Started

Run the "SheshaMMSampleAdminPortal" app that you set up in the [Quickstart Guide](https://shesha-docs.readthedocs.io/en/latest/guides/00-quickstart/) and then login. It shoulld be completely blank i.e. no menus or data in the content window.


![blank admin portal](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/membership-management-app-1.png?raw=true)


## Configuring Your Role

Before you can get started designing your app you will need to give your self the adequate role required.

Because you have not configured any navigation you will need to go to the roles section using the direct link "/administration/roles/" so if your admin portal is running on "localhost:3050" then the link would be "localhost:3050/administration/roles/".


![roles administration](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/membership-management-app-2.png?raw=true)


Because we will be configuring menus and changing system related configurations we will add our user "admin admin" to the "System Administrator" role. You can click on the magnifying glass icon in order to access the details view.


![system administrator role](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/membership-management-app-3.png?raw=true)


In the "Members" pane click on the "Add" button. This will bring up a select user popup. You can double click the "System Administrator" user and this will assign the role of System Administrator to the current logged in user.

We currently only have one user in the system with the first name "Admin" and the last name "Admin". Their full name has been saved as "System Administrator" for the sake of this demo.


![select role for user](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/membership-management-app-4.png?raw=true)



Congratulations you have now successfully assigned your user "Admin" the role required to start configuring the app


![user role list](https://github.com/Boxfusion/shesha-docs/blob/main/docs/assets/membership-management-app-5.png?raw=true)


You are now ready to move on to the next sectioin.