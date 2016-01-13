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

**Elements of the Notification Service**

The Notification Service includes a number of different components.

• Clients An external user or system that sends or receives a notification

• Publications An event handler that listens for incoming notifications

• Subscriptions An event handler that dispatches outgoing notifications

• Topics A subject that describes what the notification is about

• Protocols Methods by which FME Server can receive or send notifications

Although the diagram below shows a continuous process, from a sending client through FME Server to a receiving client, it is not necessary for all of these components to be used in a setup.

If the system is designed for FME Server to only receive notifications, then only the publications side of the diagram is relevant. Likewise, if the system is intended for FME Server to only send notifications, then only the subscriptions side of the diagram applies.

**Clients**

A client is a user or system that sends or receives a notification. The client may be a physical person, or may just be a component in a computer system.

For example, a database update might cause a trigger to send a notification to FME Server, in which case the database system is the client. But a client could also be a person who, for example, triggers a notification by sending an email to FME Server.

Since they are sending information these clients are called “Publishers”.

Likewise, FME Server can send a notification for another client system to receive. Alternatively this client can also be a real person, who might receive a notification in the form of an email.

Since they are receiving information, these clients are called “Subscribers”.