# Notifications Protocols

Different notification protocols need different parameters and set up.

**Available Protocols**

A protocol is a method of communication. There are many different protocols available in FME Server; some of them are only for use on Publications, some are only for Subscriptions, and some of them can be used with both notification types.

This table lists the different Publication and Subscription protocols and the following pages go into detail on some of the most important, excluding email, which we have already covered.

**Directory Watch Notifications**

Directory Watch is another Publication-only notification protocol.

Similar to IMAP it monitors for a new object, but instead of email it is monitoring a directory for new files to be added. When a file appears in that directory then the Topic to which it is tied becomes triggered.

The directory being monitored is one of the FME Server resources folders, and this is basically the only parameter you need to set for this notification:

This Directory Watch notification monitors the Data folder for new files.

It will not scan subdirectories because the parameter Watch Subdirectories is set to No.



<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-bolt fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">NEW</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
New for FME2015 is the ability to choose whether to watch for the creation of a new file, or the modification or deletion of an existing file. Also new is the ability to set an elapsed time between notifications. You would want to make sure this setting is longer than the time taken to copy large files onto the file system; otherwise you’ll get multiple notifications for the same file update!
</span>
</td>
</tr>
</table>

Because FME Server resource folders can be accessed through the file system, it’s possible to put new files into a folder directly, rather than having to upload them via the Web User Interface.

As usual, the notification will be passed into a workspace through a Reader, often a plain text Reader. The result will be a notification that a new (or updated) file exists, with the name of that file:

If the filename is already known then the workspace could just read from it directly (it would also need a textfile Reader to accept the notification, even if the content is not used) or it can extract the file name using a JSON transformer and read content from the file using a FeatureReader transformer:

For an example of using the Directory Watch tool, see the exercise in Chapter 5.

