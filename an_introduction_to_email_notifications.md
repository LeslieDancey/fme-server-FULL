# An Introduction to Email Notifications

An Introduction to Email Notifications Email is probably the most commonly used notification protocol

It’s important to cover email notifications in some detail because they are the most commonly used type of notification on FME Server.

“Email” is actually a protocol used by Publication and Subscription components. Email Publications receive incoming email and Email Subscriptions send outgoing email.

**Email Protocols**

FME Server can make use of email messages as both an incoming and outgoing notification protocol.

There are two email-related protocols available in FME Server: “SMTP” and “IMAP”.

The SMTP protocol is the ability to directly send or receive an email through an email server built into FME Server.

The IMAP protocol acts a little differently. It is an indirect process that connects to an email account on a server elsewhere.

When that account receives an email the IMAP protocol passes it on to FME Server.

SMTP can be used as both a Subscription and a Publication protocol; IMAP can only be used for a Publication (i.e. it can only be used to detect incoming emails).

**SMTP Publications**

SMTP Publications are when data is published to FME Server via a direct email. FME Server receives an email and triggers a Topic in response.

**Setting up an Email Publication**

Creating an SMTP publication is done in the Notifications section of the Web User Interface, by choosing the Email (SMTP) protocol for a new Publication.

Once the protocol type is selected, the publication must also be given a name and an existing topic chosen to be triggered.

The final parameter is the Email User Name; in this example it is set up to be RoadInfo.

Notice the author is suffixing the publication and topic names with _Incoming so that there is no confusion over which topics are being used for incoming notification and which ones for outgoing.

Now, whenever an email is sent to RoadInfo@serverhost.com – for example someone is sending an email to report snow on the road – the RoadConditions_Incoming topic is triggered.

**Setting up the Email Server**

SMTP email publications are possible because FME Server includes an in-built email server as one of its components. However, this does require that the server has a domain name registered with a DNS name server.

The steps to set up the email server for notifications are documented in the FME Server Reference Manual, and also in the following exercise.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Sister Intuitive says …</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
“FME Cloud instances are automatically configured for email
notification, and have a public domain name too, so you don’t need
to do any additional setup.”
</span>
</td>
</tr>
</table>

**IMAP Publications**

IMAP (Internet Message Access Protocol) is a variation on email for incoming (Publication) notifications.

Instead of using the in-built email server, an IMAP Publication connects to another email server and monitors it for incoming email. When an email arrives in that account then the Topic to which it is tied becomes triggered.

Setting up an IMAP Publication

Like the SMTP protocol, IMAP Publications are set up in the Notifications section of the Web User Interface, by creating a new Publication and choosing the Email (IMAP) protocol.

Here are the parameters for an IMAP Publication:

Notice that most parameters are for defining the IMAP (Email) server connection.

Two important parameters let you decide the interval to check for emails and decide whether to fetch all unread emails or new emails only.

There is also a parameter to select an FME Server resource location in which to store any email attachments:

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Monsieur D. Server says …</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
“Most email servers support IMAP functionality, as do the majority
of cloud-based email providers such as Gmail, Outlook.com, Yahoo!,
etc; so it’s very easy to have FME Server scan a Gmail account for
incoming mail, and then act on its contents.”
</span>
</td>
</tr>
</table>

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 4A </span>
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
<td style="border: 1px solid darkorange">n/a</td>
</tr>

</table>