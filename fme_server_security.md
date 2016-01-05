# FME Server Security

FME Server includes security to prevent unauthorized users from accessing services and other resources.

All security information for FME Server is stored in the repository database and is managed using the FME Server Web User Interface.

The key to setting up FME Server security is to have a clear plan on which services and accounts will be provided with open access, and which need to be restricted.

These policies are then set up using the Security section of the Web User Interface.

**Roles and Users**

Security is implemented using a system of roles and users. A role is best described as a function of the person; for example user, author, or administrator. Each user account is associated with one or more roles.

A default set of roles and user accounts is defined when FME Server is installed:

For example, in the previous example, if you logged in using the admin account, then you have both the role of fmeadmin and fmesuperuser.

Rather than apply security settings to individual users, FME Server allows you to apply them to specific roles. That way the settings can be changed for multiple users at once.

The role is selected under the Role Policies tab:

**Security Policies**

There are various sections of security policies that can be set for each role.

**General**

These are general policies such as the ability to manage jobs, services, and security. For example, if you don’t have the ability to manage security, that item will be missing from the main menu of the user interface.

**Topics**

Topics are related to Notifications, which we’ll cover later. Different capabilities – read, write, publish, remove – can be assigned for each topic you create.

**Resources**

Resources are files and datasets stored on FME Server. Different permissions – read, write, upload, delete – can be assigned to each resource.

**Services**

Services are key items of functionality on FME Server. They are the different methods by which a workspace can be run and output data delivered. Each role can be allowed – or not – to use a particular service.

**Repositories**

As you know, repositories are a place to store and categorize workspaces. Each role can be given different permissions for each and every repository.