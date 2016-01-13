# The Notification Service

The Notification Service is a way for data to be pushed to and from FME Server in the form of short messages.

**What is a Notification?**

A notification is a simple message (sometimes called an “alert”) that informs someone or something that a particular event has happened.

Notifications on FME Server can occur in two different forms; incoming and outgoing.

Incoming notifications alert FME Server to an event that has taken place elsewhere.

Outgoing notifications alert users to an event that has taken place on FME Server.

In this way, FME Server can take action in response to an event notification, or a user can take action in response to a notification from FME Server.

The **Notification Service** is the part of the FME Server architecture that handles incoming and outgoing notifications.

**When to Use Notifications**

Notifications should be used when you want to trigger an FME Server response to an event that is reported from outside of FME. The event should not be a continuous series of messages; if there is more than one message per second you should consider using Message Streaming techniques instead.

Notifications are also for when you want to send a message about something that happened on FME Server, to an outside subscriber. Again, if there is likely to be more than one message per second you should consider using Message Streaming.

In either case a notification is for sending a brief message, usually in order to trigger an action from the recipient. It’s not intended to be used for transmitting large amounts of spatial data. At most you should use it for a single geographic feature such as a point location.