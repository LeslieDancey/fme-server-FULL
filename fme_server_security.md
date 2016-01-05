# FME Server Security

FME Server includes security to prevent unauthorized users from accessing services and other resources.

All security information for FME Server is stored in the repository database and is managed using the FME Server Web User Interface.

The key to setting up FME Server security is to have a clear plan on which services and accounts will be provided with open access, and which need to be restricted.

These policies are then set up using the Security section of the Web User Interface.

**Roles and Users**

Security is implemented using a system of roles and users. A role is best described as a function of the person; for example user, author, or administrator. Each user account is associated with one or more roles.

A default set of roles and user accounts is defined when FME Server is installed:

For example, in the previous example, if you logged in using the admin account, then you have both the role of fmeadmin and fmesuperuser.