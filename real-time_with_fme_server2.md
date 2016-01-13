# Real-Time with FME Server

Real-Time systems are those that act on events as they happen, and send information as it becomes available.

**What is Real-Time?**

In real-time FME Server is either set up to receive incoming information in the form of notifications, messages, and alerts, or to send information in a similar format.

Real-time is often implemented to monitor sensor networks, run event-driven processing, and/orto send alerts to mobile devices such as cell phones.

Therefore real-time is usually related to small amounts of information, rather than large datasets,which can arrive either individually or as a continuous communication stream.

Real-world examples include processing simple location data from a vehicle tracking system, or handling a continuous stream of data from a temperature sensor or lightning detector. A simpler example would be sending email to a system administrator in response to database table updates.

Real-time data in FME is handled in two ways: Notifications and Message Streams.

**Notifications**

Notifications are how FME Server handles individual messages and alerts.

FME Server has a specific Notification Service that can be set up to listen for an incoming message from outside of FME, and trigger a certain action in response; or that can be set up to send a single alert in response to an event that takes place on FME Server.

Protocols supported include email, websockets, and notifications for Apple and Android devices.

**Message Streams**

Message Streams are how FME Server handles a continuous flow of information; literally thousands of messages per second.

Rather than use the Notification service, message streams are handled by a number of transformers. A workspace is set up to run continuously and the transformers within it listen for, and dispatch, messages on a number of different protocols.

Protocols supported include TCP, JMS, and HTML5 WebSockets.