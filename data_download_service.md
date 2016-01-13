# Data Download Service

The Data Download service is the key tool for Self-Serve setups

**What is the Data Download Service?**

When you run a workspace with the Job Submitter service (as in Chapter 2) the data is written to the location specified by the workspace; for example a file, directory, or database.

The Data Download service instead writes the output to a zip file and presents the user with a link to that file. This makes it ideal for self-serve, because the data is delivered directly to the user.

**Creating a Data Download Service**

A workspace becomes available for data download use when the author registers it against the Data Download service when publishing it to FME Server.

**Using a Data Download Service**

Once registered this way, Data Download options become available in the FME Server Web interface for that particular workspace. 

The workspace can be run through the web user interface, or using the developer URL information.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Monsieur D. Server says...</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
‘Behind the scenes, the Data Download service overrides the
Writer’s destination parameter and writes a zip file to an internal
folder, from where it can serve up the required data to the enduser
in the form of a URL’
</span>
</td>
</tr>
</table>