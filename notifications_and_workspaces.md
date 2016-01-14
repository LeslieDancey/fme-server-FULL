# Notifications and Workspaces

Workspaces are what make FME Server the ideal engine for Spatial Data notifications

**Message Transformation**

As shown in the previous exercise, the simplest setup for the FME Server Notification Service is an incoming message (Publication) tagged with a specific topic that gets passed as an outgoing message to any Subscription registered with that topic:

However, that scenario does not include any transformation – restructuring – of the message contents. If the message needs to be processed in some way then an FME workspace can be employed between Publication and Subscription.

A workspace is the key functionality of FME and with one you can read spatial data from a message, in almost any format, carry out spatial transformations on that data, and then pass on the results to a set of subscribers.

This blend of live messaging with Spatial ETL is unique.

In this scenario a workspace is literally a Subscriber to the incoming Publication, and receives the message content from it. The workspace then acts as a Publisher, sending an outgoing message to any Subscribers.