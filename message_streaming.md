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