# Automated Data Processing

Automated Data Processing is an unscheduled, but automatic, workspace process.

**What is Automated Data Processing?**

Automated Data Processing is when a workspace is run in response to an event, rather than on a schedule. Because the time of the event cannot be predicted, the workspace is not run at a set time. It is automatic, but unscheduled.

**Setting up Automated Data Processing**

There are two common methods by which to automate FME Server in response to an event:

• Notifications

• REST API

**Automated Data Processing with Notificiations**

If you’ve just finished Chapter 4 – which covered notifications – the most obvious way to set up Automated Data Processing will be through a notification.

In this scenario, a Publication is set up to trigger a topic. The workspace is tied to the topic so that it is run as the topic is triggered.

Although the workspace can also send an outgoing notification, here we’re concentrating on the idea of starting the workspace, not what it does.

Here we aren’t really talking about events that need to be processed; this is more the case that a given event starts a larger processing task.

For example, a system administrator might send an email to FME Server to inform it a daily update of database tables is ready to run. The content of the email isn’t important, just the fact that it is triggering a translation.

In this way a workspace can be started through protocols such as Email, Directory Watch, or JMS.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Mrs. Dee B. Emess says…</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
“You can set up a trigger to call FME Server for each individual
addition/edit to a record, or you can use a Bulk Mode, which is
useful when a large number of edits are made that can be
processed by a single workspace.
FMEpedia has some great examples of Single and Bulk processing
for Oracle, SQL Server, and PostGres/PostGIS.”
</span>
</td>
</tr>
</table>