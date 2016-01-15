# Notifications and Workspaces

Workspaces are what make FME Server the ideal engine for Spatial Data notifications

**Message Transformation**

As shown in the previous exercise, the simplest setup for the FME Server Notification Service is an incoming message (Publication) tagged with a specific topic that gets passed as an outgoing message to any Subscription registered with that topic:

However, that scenario does not include any transformation – restructuring – of the message contents. If the message needs to be processed in some way then an FME workspace can be employed between Publication and Subscription.

A workspace is the key functionality of FME and with one you can read spatial data from a message, in almost any format, carry out spatial transformations on that data, and then pass on the results to a set of subscribers.

This blend of live messaging with Spatial ETL is unique.

In this scenario a workspace is literally a Subscriber to the incoming Publication, and receives the message content from it. The workspace then acts as a Publisher, sending an outgoing message to any Subscribers.

Of course, the above diagram shows the full potential of a notification system. It would be just as appropriate to have a system that triggered a workspace in response to a Publication, but without the workspace sending an outgoing message:

Similarly, it’s just as appropriate to have a workspace that is run by some other means, and which sends an outgoing message to a Subscription when it is complete:

For example, a workspace might be started as a scheduled task.

When the task is complete FME sends a notification email to inform an administrator.

**Workspaces as a Subscription**

When a workspace needs to react to an incoming notification it is done by connecting the workspace to a particular topic. The workspace is run in response to that topic being triggered by a Publication.

In effect, the workspace is subscribing to that topic.

In this case the message is received and passed into the workspace for processing.

**Registering a Workspace**

A workspace is set up to receive messages when it is published to FME Server and registered with the Notification service.

The Service is initially highlighted in red because there are several parameters that need to be set before it can be used.

Two important parameters are Subscribed Topics and Notification Reader

**Subscribed Topics** tells FME which notification topics should trigger the workspace.

**Notification Reader** tells FME which Reader should receive the notification content.

In this example any incoming message that is flagged under RoadCondition will cause the workspace to run. The message content will be funneled through a plain text Reader called – appropriately enough – IncomingMessage.

**Managing Workspace Subscription**

Once a workspace is published and registered with the notification server as a subscriber it appears in the Notification section of the Web user interface.

The workspace appears as a Subscription because it is literally subscribed to the topic(s) shown.

It is listed with the protocol "push" because FME Server is pushing a notification using HTTP post to run the workspace.

Clicking on the subscription allows you to make edits to the notification without having to republish the workspace; for example topics can be added or removed.

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 4B </span>
</td>
<td style="border: 2px solid darkorange;background-color:darkorange;color:white">
<span style="color:white;font-size:x-large;font-weight: bold">Basic
Notifications
and
Email
Subscription</span>
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
<td style="border: 1px solid darkorange">Provide
email-­‐driven
self-­‐serve
access
to
image
files</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Demonstrates</td>
<td style="border: 1px solid darkorange">Email
Publications
and
Topic
Notification</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">n/a</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise4b-­‐Complete.fmw</td>
</tr>

</table>

This exercise continues setting up a system that provides email-driven access to image files. In this part we’ll create a workspace that will run in response to the incoming notification.

**1. Create a Workspace**

Now we have a Publication and a Topic that it will trigger when FME Server discovers a new email in the defined email account. However, at the moment there is nothing subscribed to that publication to act upon it. We’ll handle that part of the solution with a workspace.

Start FME Workbench. Begin with a blank canvas and simply add a Creator transformer. This will give us a workspace to run in response to an email; albeit one that doesn’t do much yet.

Save the workspace as Exercise4b.fmw

**2. Publish Workspace**

Now let’s publish the workspace to FME Server. Start the Publishing Wizard using File > Publish to Server on the menubar. When prompted enter the same connection parameters as before.
Publish the workspace to the Training repository. There are no data files that need to be published along with the workspace.

In the services dialog put a checkmark in the Notification Service’s box. Click Edit to see the Service Properties for this service.

Click the […] button next to Subscribe to Topic(s) to retrieve a list of available topics from the server.

Select the ImageProcessing topic created in exercise 4a.

All other parameters can be left as they are, so simply click OK to close the dialog.

Then click Publish to finish publishing the workspace.

**3. Confirm Subscription**

Remember, the workspace is now effectively a subscriber to the email publication. To confirm this, return to the web interface. Select Notifications from the Manage menu and then click the Subscriptions tab.

You should see a push subscription for your workspace associated with the topic ImageProcessing. Click on the subscription to view the details.

Click Cancel as we don’t need to make any changes to this component.

**4. Send an Email**

As before, send an email to trigger the notification and monitor the topic to ensure that it arrives.

**5. Confirm Notification**

To confirm the notification has caused the workspace to run, open the web interface to FME Server and click the Jobs option on the Manage menu. You should see a completed job for workspace Exercise4b.fmw, where FME ran the workspace in response to the email you just sent.

Congratulations! You have now triggered an FME Server notification using email.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Mr. Flibble says …</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
“If you’re using IMAP then this is probably a good point to go back
to Notifications > Subscriptions, select the Exercise4b push
subscription, and unsubscribe it from the ImageProcessing topic.
If you don’t do this, then forever more any incoming email to your
account will trigger this workspace! And any attachments would
get stored in the Resources folder. Wouldn’t that be funny! Ha ha!”
</span>
</td>
</tr>
</table>

**Message Content**

The ability to interpret and process message content is a key reason for using FME workspaces as a subscriber. They can receive the message and then transform it in whatever way is required.

Content is received in a workspace by a Reader.

When the workspace is run (in response to a message) the notification content is substituted in place of the source dataset for a Reader feature type, so that a feature emerges from that reader with the message content attached as an attribute.

**Content Format**

Notification content can be read by a workspace in one of the following formats:

• JSON (Javascript Object Notation)

• XML (Extensible Markup Language)

For example, here a workspace has a Reader that will receive the message content.

Notice that the above workspace uses a Text File Reader.

Reading the incoming message as plain text is the most flexible method because the message is kept intact inside a single attribute and not processed into features. It would also allow you to create one workspace that could deal with both content formats.

The message can then be scanned and processed with a number of different transformers. If the messages are in JSON format there are transformers such as the JSONExtractor and JSONFlattener. Similarly there are XMLFlattener and XMLFragmenter transformers for XML content.

**Handling Email Publications in a Workspace**

As previously described, content from a notification will be passed into the workspace to a Reader, usually a plain text Reader, and stored in an attribute.

For a JSON email the content will look like this:

{
"fns_type": "email_publisher",
"email_publisher_to": "demo@somehost.com",
"email_publisher_subject": "MIME message from sender",
"email_publisher_content{0}": "Testing Email",
"email_publisher_content_type{0}": "text/plain",
"email_publisher_from": "sender@somehost.com",
"email_publisher_received": "Thu May 17 11:15:46 PDT 2012",
"email_publisher_sent": "Thu May 17 11:15:46 PDT 2012",
"email_publisher_attachment{0}": "C:\\Temp\\demo246129673106713_canada.xsd"
}

Notice how it includes the email from and to fields, plus the content itself. If there are attachments they will be stored on the file system and a path substituted into the JSON content.

This content can be converted into FME attributes using the JSONFlattener transformer:

The result – as shown in the FME Data Inspector – will look something like this:

Now the content is available to the workspace and can be processed as required.

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 4C </span>
</td>
<td style="border: 2px solid darkorange;background-color:darkorange;color:white">
<span style="color:white;font-size:x-large;font-weight: bold">Basic
Notifications
and
Email
Subscription</span>
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
<td style="border: 1px solid darkorange">Provide
email-­‐driven
self-­‐serve
access
to
image
files</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Demonstrates</td>
<td style="border: 1px solid darkorange">Email
Publications
and
Topic
Notification</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise4c-­‐Begin.fmw</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise4c-­‐Complete.fmw</td>
</tr>

</table>

Having already set up a solution for incoming email notifications (in Exercise 4b) we can now expand upon that to let the user select a neighborhood in the email subject line. This neighborhood will be used to select a feature to clip the data with.

**1. Open the Starting Workspace**

In FME Workbench open the starting workspace for this exercise.

You must open this workspace as the exercise does not continue on from Exercise 4b. This workspace has more content and is similar to those created in Chapter 3; it reads and resamples raster data, clips it to a boundary, and writes it to a JPEG file.

**2. Add a Text File (TEXTLINE) Reader**

To read information into a workspace, from a notification, requires the use of a Reader. In this case we’ll use a Text File Reader.

Select Readers >Add Reader from the menubar and add a Text File reader using the following settings:

Source Format: Text File

Source Dataset: C:\FMEData2015\Resources\emailIMAP.json

Parameters:Read Whole File at Once: Yes

The Read Whole File parameter is VERY important! Click OK and OK again to add the Reader.

The file being read here is provided because all Readers need a source dataset, but also as an example of what Notification Service sends to a workspace when FME Server receives an email.

Examine the file in a text editor. It contains JSON content. You can see a number of JSON attributes available, which come from an email, and you will be able to read and use any of these in a workspace. In this exercise we’ll be using the Subject of the email.

Because you set the Parameter to read the whole file at once, all of the contents will be read into a single attribute in a single feature, rather than creating multiple features.

**3) Process the JSON Message**

Back in the workspace, connect the Text Line source feature type to the JSONFlattener already in the workspace.

Click the cog wheel icon to open the parameters dialog for the JSONFlattener.

Examine the parameters. This transformer flattens the JSON attributes into FME attributes and exposes all of them.

Browse through the rest of the workspace. It also reads a KML dataset of neighborhood polygons and then filters the neighborhood by the subject of the email to clip by that neighborhood. The UnconditionalFeatureMerger is a custom transformer (available on the FME Store) that simply merges data together without any matching key.

**4) Test the Workspace in FME Workbench**

Test the workspace by running it in FME Workbench.

This will work because the text file contains a sample email where the neighborhood is coming from the email_publisher_subject attribute. If you wish, you can edit the file and use either “Downtown” or “West End” as the neighborhood.

Inspect the output. It should look like this:

**5) Set Writer Path**

Set the JPEG writer path to the Output folder of Server Resources.

**6) Publish to FME Server (Step 1)**

Start the Publish Wizard from the menu or toolbar and enter the connection parameters when prompted. Select the Training repository to store the workspace, as usual.

Click the Select Files button in the dialog and ensure that only the KML dataset VancouverNeighborhoods.kml gets uploaded to the repository.

The easiest way to do this is to click the Files/Folders box to turn off ALL files, and then simply turn the neighborhoods file back on:

Uncheck the GeoTIFF files if they are checked because they are already available in the FME Server Repository.

However, you will still need to point the file location from the workspace to the resource location.
This is necessary because there is no end-user to set this – for example in a published parameter.

Therefore, click OK. A dialog will appear in which you are warned that the file references are not valid. For each of the Orthophoto references, click the […] ellipsis button and browse to the true file location in the resources folder.

When a reference is fixed then it will show as pointing to the resources folder; for example Data/Orthophotos/02-03-HI.tif

Once complete for all files, click OK and then click Next to go on to the next publishing stage.

**7) Publish to FME Server (Step 2)**

In the Services dialog check the Notification Service and click Edit to open the Service Properties.
Choose the topic ImageProcessing you created in the previous exercise as the Subscribed Topic.
The Notification Reader should be set to the Reader (emailIMAP[TEXTLINE]).
This way the content of any incoming email will be passed directly to that Reader.

Click OK and then Publish to complete the wizard.

**8) Send an Email to FME Server**

As before, use any method you like to send an email to your FME Server.
Use the email address you used in Exercise 4a/4b. Enter either Downtown or West End as the subject of the email.

**9) Confirm Workspace Triggered**

Again, if you are using IMAP it make may take a couple of minutes until FME Server is notified.

Open the Web User Interface and click on the Jobs link and to view the Jobs history. Look for a completed job where FME Server ran Exercise4c.fmw in response to the email. Check the Resources/Data/Output directory for your imagery.

Congratulations! Now users can email your FME Server with specific information on how to run a workspace - this is truly Self-Serve! In this next exercise you will configure FME Server to email the user back a result.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Mr. Flibble says …</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
“Again, you’ll probably want to unsubscribe Exercise4c from the
ImageProcessing topic if you’re using IMAP. Unless you want all
incoming emails to keep triggering this workspace again and again
and again and again and again and again and again …”
</span>
</td>
</tr>
</table>

**Email Subscriptions**

Email Subscriptions are when FME Server sends an email in response to a Topic. The in-built mail server in FME Server is only for incoming mail, and so messages need to be sent via an existing SMTP email server.

**Setting up an Email Subscription**

Creating an Email subscription is done in the Notifications section of the Web User Interface, by choosing the email protocol for a new Subscription.

Here, for example, the author has chosen the Email protocol for a new Subscription.

The Subscription is given a name and an existing topic chosen to be triggered.

There are many more parameters for outgoing mail because the full SMTP server connection parameters need to be defined.

Now when the RoadConditions_Out topic is triggered, an email is sent to recipient@example.com

However, the various fields for the email itself (From, To, Subject, Template) do not need to be hardcoded and can be passed through to the Subscription from a workspace.

One other important parameter is the Email Format.
This can either be plain text or HTML.

**Workspaces as a Publication**

When a workspace acts as a Publication, it triggers a topic when it is run.

In effect, the workspace is publishing to that topic.

In this case the message is constructed in the workspace and passed onto the Subscription.

Publishing notification messages from FME is useful for both sending messages containing content from the data being processed, and for reporting the status of a translation, such as whether it has run successfully or ended in a failure.

**Message Content**

The ability to construct message content from a variety of sources – including spatial – is a key reason for using FME workspaces as a publisher. Workspaces can transform data in multiple ways, use it to construct a message, and then dispatch that message to users as a notification.

Content is sent from a workspace by a Writer.

When the workspace is run the notification message is constructed as an attribute and sent to a Writer feature type. The output from that feature type is used by the notification service as the content of the publication.

**Content Format**

For the purposes of FME notifications, the content of a workspace publication can be in any format. It does not necessarily need to be either JSON or XML, though obviously it would have to be if any client who subscribes to the notifications requires it in that format.

For example, here a workspace constructs a plain-text weather (lightning) alert using an AttributeCreator:

Now the message attribute is connected to a Text File Writer in order to provide a means for publishing the outgoing message.

**Registering a Workspace**

Setting up a workspace to communicate notifications is achieved when the workspace is published to FME Server.

Notifications are sent once the workspace is complete. The way in which the workspace is run is not important. Notifications can be sent for workspaces run using the Job Submitter Service, or the Data Download Service, or any other service.

In other words, a workspace that sends notifications doesn’t need to be published to the Notification service; it should be published to the service under which it is to be run. Under the properties for that service will be parameters for setting the notification.

In this example the author is publishing a workspace to the Job Submitter service and has opened the properties dialog for that service. There are two parameters for controlling the topics – one for success and one for failure – and a parameter for specifying the Writer to use.

Having two Topic parameters is useful because different notifications can be sent depending on whether the workspace succeeds or fails.

In this case, when the workspace runs to completion it will trigger the RoadConditions_Out topic.
If the workspace fails to complete, it will trigger the WorkspaceFail topic.

Either way, the outgoing message is set to be output via a TextLine Writer defined in the workspace.