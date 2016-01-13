# Format Selection

Another obvious requirements in Self-Serve is to be able to select the format of data to be downloaded

One of the most useful parameters in a self-serve system controls the output data format. With a simple Generic format, FME allows the end-user to select this format on the fly, without any format-specific setup from the workspace author.

**The Generic Writer**

The Generic writer is a way to write data in FME where the output format is chosen at run-time.
This way a workspace may be created that can write to any format.

The output format is defined by a parameter so, by publishing the parameter, the user gets to choose the output format at run-time.

There are a couple of points to keep in mind when using the writer:

• The parameter for output format is automatically published, but in FME Server’s interface it appears only as a text field that accepts FME’s short form name for any format. Best practice decrees this should usually be replaced by a new Choice with Alias parameter; to reduce the list to a reasonable set of choices, with descriptive format names.

• Each writer format has its own specific parameters, and these may still need to be set when a generic writer is used. For example, a specific template file might need to be used when AutoCAD is chosen as the output format. This can be achieved by adding a writer of the same format and setting the parameters in that writer. The Generic writer will inherit the parameters of this dummy writer, even if no features are connected to it.