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

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 3B </span>
</td>
<td style="border: 2px solid darkorange;background-color:darkorange;color:white">
<span style="color:white;font-size:x-large;font-weight: bold">Data
Download</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Scenario</td>
<td style="border: 1px solid darkorange">Airphoto Data Vendor</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Data</td>
<td style="border: 1px solid darkorange">GeoTiff Orthophotos</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Overall Goal</td>
<td style="border: 1px solid darkorange">Create
a
data
download
service</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Demonstrates</td>
<td style="border: 1px solid darkorange">Authoring
for
and
Using
the
Data
Download
Service</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise3b-­‐Begin-­‐
DataDownload.fmw</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise3b-­‐Complete-­‐
DataDownload.fmw</td>
</tr>

</table>

This exercise involves making orthophoto data available through a Data Download service. We will also mosaic the various files together and resample them to a lower resolution.

**1. Start Workbench**

Start Workbench (if necessary) and open the starting workspace for this Exercise. You will be familiar with it as it is the same workspace we created in Chapter 2.

**2. Delete Existing Published Parameters**

Some parameters in a workspace are published by default. This lets the user select the output
dataset (for example) when the workspace is run. However, we don’t need to let the user set any
parameters and so best practice suggests we remove them.

Browse the Navigator window and expand the section labelled User Parameters - Published Parameters. Right-click and delete the Feature Types to Read parameter.

Only keep the published parameter for the source dataset.