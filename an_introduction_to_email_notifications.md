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

SMTP Publications are when data is published to FME Server via a direct email. FME Server
receives an email and triggers a Topic in response.
Setting up an Email Publication
Creating an SMTP publication is done in the Notifications section of the Web User Interface, by
choosing the Email (SMTP) protocol for a new Publication.
Once the protocol type is selected, the
publication must also be given a name
and an existing topic chosen to be
triggered.
The final parameter is the Email User
Name; in this example it is set up to be
RoadInfo.
Notice the author is suffixing the
publication and topic names with
_Incoming so that there is no confusion
over which topics are being used for
incoming notification and which ones for
outgoing.
Now, whenever an email is sent to
RoadInfo@serverhost.com – for
example someone is sending an email
to report snow on the road – the
RoadConditions_Incoming topic is
triggered.
Setting up the Email Server
SMTP email publications are possible because FME Server includes an in-built email server as
one of its components. However, this does require that the server has a domain name registered
with a DNS name server.
The steps to set up the email server for notifications are documented in the FME Server
Reference Manual, and also in the following exercise.