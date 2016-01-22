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

**Web Automation Services**

Web Automation Services are those such as IFTTT and Zapier, which tie together different webbased applications using conditional statements.

Such services allow you to define a statement using a trigger (the  If part) and an action (That).

For example, here is a pre-defined IFTTT “recipe” to send an email when congress is about to vote on a bill.

Typically intended to support tools like Gmail, Dropbox, and Facebook; it’s also possible to connect FME Server into a workflow like this.

For example, a Zapier “zap” looks like this:

Here, whenever a tweet with a specific keyword and location is discovered, a workspace is run on FME Server.

In this example the search term is for the word “earthquake” and the location is defined (not shown here) as within 50km of the city of Vancouver, BC.

The FME workspace being run is called EarthquakeResponse.fmw and the Text File Reader within it is being fed the coordinates of the tweet:

Now Zapier will check for such a tweet (by default every 15 minutes) and run the workspace on FME Server in response:

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 5B </span>
</td>
<td style="border: 2px solid darkorange;background-color:darkorange;color:white">
<span style="color:white;font-size:x-large;font-weight: bold">Automated
Data
Processing</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Scenario</td>
<td style="border: 1px solid darkorange">Airphoto
Data
Vendor</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Data</td>
<td style="border: 1px solid darkorange">GeoTIFF
Orthophotos</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Overall Goal</td>
<td style="border: 1px solid darkorange">Run
a
translation
workspace
whenever
new
data
is
added</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Demonstrates</td>
<td style="border: 1px solid darkorange">Automated
Scheduling</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise5b-­‐Begin.fmw</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise5b-­‐Complete.fmw</td>
</tr>

</table>

As a member of the Airphoto Data team, you would like to have FME start processing data once an update becomes available, and an email to be sent to alert you of this. Availability of new data will be denoted by new files in a folder. The Directory Watcher protocol can be used to do this.

**1. Create New Topic**

In the Notifications dialog create a new Topic called NewData.

**2. Create a New Publication**

Now create a new Publication. Use the following settings:

Publication Name: New Data Watcher 

Topic to Publish to: NewData (the topic you created in step 1)

Protocol: Directory Watch

Directory to Watch: Browse Resources \Orthophotos and check it

Filter: Create (remove Modify and Delete)

