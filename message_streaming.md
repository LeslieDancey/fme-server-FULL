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