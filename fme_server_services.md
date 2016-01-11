# FME Server Services

Many standard operations using FME Server take place using something called a ‘service’. FME Server provides a wide range of services to carry out common tasks.

What is a Service?

In the simplest of terms, a service is a piece of software that handles communications between a client and a server. In other words, it’s a tool that allows users to access complex functionality through a simplified interface.

In terms of FME Server, the client is often—but not always—a web browser that passes requests to FME Server using a service.

For FME Server, a service lets you send specific types of requests to FME Server and provide results to client applications in a specific way.

For example, instead of just running a workspace, you can have a web page ask for the results of the workspace as a package of data compressed in a zip file.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Professor Spatial F.M.E., E.T.L. says...</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
‘Although the concept sounds complicated, a service is a simpler way of
communicating requests to FME Server than using the API.
Also, FME Server includes a number of predefined services that cover a
lot of the functionality you are likely to need.’
</span>
</td>
</tr>
</table>

**Available Services**

FME Server includes the following services:

Remember that services can communicate in both directions. Transformation services – for example Data Download – are primarily Self-Serve tools for Server to deliver data to the end user.

Utility services can be described as “helper” services. They interact with FME Server to assist in menial tasks such as uploading data or providing token security. In most cases these are facilities that an author or developer will be using in a way that’s hidden from the user.

The Notification Service is used for passing short messages into and out of FME Server. Incoming messages notify FME Server to take some action, whereas outgoing messages alert an end-user (or system) that some sort of event has occurred.

**Workspaces and Services**

When a workspace is published to FME Server it can be registered with a particular service.

The Job Submitter service is automatically selected in the FME Server publishing wizard, whenever a workspace is published, but many other services are available too.

Registering a workspace with a service makes the workspace available for use in that service although, as you’ll discover, not every workspace is capable of being used by every service.

Be aware of the Edit button to the right of each service.

Every service has a set of parameters available that determine how a workspace will be run with that service.

These parameters include ones for notification topics to trigger on completion of the workspace.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-info-circle fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">TIP</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
It’s important to understand that a workspace may be registered against one
service, many services, or no services at all.
</span>
</td>
</tr>
</table>

When a workspace is not registered against a service, you can run it as a regular translation using the FME Server Console or the FMEServerJobSubmitter transformer in Workbench.

When a workspace is registered against a service, it can be used by that service and it’s still available for use as a regular translation using FME Server Console.