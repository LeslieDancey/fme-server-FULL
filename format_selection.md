# Format Selection

Another obvious requirements in Self-Serve is to be able to select the format of data to be downloaded

One of the most useful parameters in a self-serve system controls the output data format. With a simple Generic format, FME allows the end-user to select this format on the fly, without any format-specific setup from the workspace author.

**The Generic Writer**

The Generic writer is a way to write data in FME where the output format is chosen at run-time.
This way a workspace may be created that can write to any format.

The output format is defined by a parameter so, by publishing the parameter, the user gets to choose the output format at run-time.