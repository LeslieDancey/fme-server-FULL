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