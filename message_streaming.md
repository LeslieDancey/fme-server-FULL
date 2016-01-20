# Message Streaming

Whereas Notifications are one-off messages, Message Streaming involves a continuous flow of information

**What is Message Streaming?**

Message Streaming is a real-time technique that involves a continuous flow of information.

For our purposes, “continuous” means messages arrive at the FME Server at a faster rate than the notification service could handle; say more than one message per second.

At rates faster than this the notification service does not have time to start and run a workspace to process each message. However, a message stream uses a workspace that is constantly running, and doesn’t need to be started for each message, and so can process data at a much faster rate.

When used in this way we call it High Capacity Message Streaming, as thousands of messages can be processed every second.

**Elements of a Message Stream**

Like Notifications, Message Streams can be either into or out of FME, or both:

However, rather than use the Notification service with Readers and Writers, Message Streams are handled by a number of transformers. A workspace is set up to run continuously and the transformers within it listen for, and dispatch, messages on a number of different protocols.

Key protocols supported include:

A workspace containing any of the Message Streaming transformers will run continuously because the transformer itself is designed to run continuously.

**Receiver** transformers will emit a feature in response to an incoming message, but will then return to waiting for more messages. Even if no messages are instantly available, it will not terminate.

**Sender** transformers will send a message in response to an incoming feature, but will then return to wait for more features. Again it will not terminate until the workspace is deliberately stopped.

**Message Streaming Architecture**

A Message Streaming architecture that both receives and sends messages looks like this:

- A stream of messages is read into the workspace via one of the available transformers, for example the JMSReceiver.

- Data is processed by any of the available FME transformers, according to the needs of the setup.

- A stream of messages is sent out of the workspace via one of the available transformers, for example the TCPIPSender.

The Database components in this diagram are optional, but probably usual.

Data read from the database is intended to be used to process the incoming message. For example perhaps the message represents a point feature (maybe a vehicle location) that is used to filter database data (maybe traffic conditions) against.

Data written to the database is usually to record a stream of message information. For example, perhaps each incoming message represents a point feature (a lightning strike) that needs to be recorded in a database.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Ms. Analyst says …</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
“Writing to a database requires that the transaction interval is set
to 1. Otherwise messages won’t get committed as they arrive.”
</span>
</td>
</tr>
</table>

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 4E </span>
</td>
<td style="border: 2px solid darkorange;background-color:darkorange;color:white">
<span style="color:white;font-size:x-large;font-weight: bold">Message
Streaming</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Scenario</td>
<td style="border: 1px solid darkorange">Airphoto Data Vendor</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Data</td>
<td style="border: 1px solid darkorange">GeoTiff Orthophotos</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Overall Goal</td>
<td style="border: 1px solid darkorange">Web
Map
Application
with
WebSockets</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Demonstrates</td>
<td style="border: 1px solid darkorange">WebSockets</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise4e-­‐Begin.fmw
C:\FMEData2015\Workspaces\ServerAuthoring\Exercise4e-­‐Begin-­‐Advanced.fmw</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">n/a</td>
</tr>

</table>

This exercise uses FME Server’s WebSockets service and WebSockets transformers to power a Web Map application. The method shown here is suitable for high frequency messaging in excess of 1 message per second.

**1. Open the Starting Workspace**

In FME Workbench open the starting workspace Exercise4e-Begin.fmw

Notice that it contains two WebSocket transformers – one for receiving and one for sending. The workspace will listen for information coming through the WebSockets channel. Incoming data will be processed with an offset in its coordinates, and then sent back. The workspace will run continuously, processing each incoming message, until stopped manually.

**2. Update Server Name**

The first task is to update the hostname for the server to match the one you are using.

Locate the published parameter server_url in the Navigator window.
Double-click the parameter to open it for editing and replace the host with your own FME Server host name and port. It will need a “ws” prefix to denote the WebSockets protocol.

If you are working on the same machine as your FME Server you can use localhost for example: ws://localhost:7078/websocket