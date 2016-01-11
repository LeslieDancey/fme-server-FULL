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