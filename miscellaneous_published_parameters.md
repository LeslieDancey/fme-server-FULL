# Miscellaneous Published Parameters

Self-Serve parameters can include any regular parameters, not just ones that are specific only to a Data Download setup

Any parameter in FME can be published and presented to the user as a choice to be made when running a workspace. They don’t have to be specifically related to the Data Download service.

**Finding a Parameter**

Parameters are located in the Navigator window (usually on the left-hand side of FME Workbench).

As you can see, there are parameters for the source data location (1) and the destination data dataset (2), which is the one that the Data Download service overrides. There are also general Reader and Writer parameters (3) and parameters for transformers (4)

**Publishing a Parameter**

Parameters are published by right-clicking on them and choosing “Create User Parameter”.

For example, here a workspace author is about to publish a parameter on the LabelPointReplacer transformer.

When the workspace is run the end-user will now be able to decide what size they want labels to appear as.

The author gets to choose the type of parameter (in this case a floating point number), the user prompt, and the default value.

**Using a Parameter**

A User Parameter that is published becomes available to the end-user at run-time.

In FME Workbench, you would select Run > Prompt and Run from the menubar, to see these parameters. There is also a toolbar button and a keyboard shortcut (Ctrl+R).

In FME Server, these parameters become available on the Configuration page of a service, as seen in the Chapter 2 exercises.

**Key Parameter Types**

Two key parameter types for a self-serve setup are “Choice with Alias” and “Scripted”.

Choice with Alias parameters are where the user is presented with a choice, each of which returns a different value to FME.

For example, here the author wishes the user to select the height of labels to be created in the output dataset.

The user is presented with the list of (more intuitive) options on the right, but the value returned to FME will be the (more useful) number on the left.

This parameter type is also very useful for some Data Download specific tasks, as we’ll see shortly.

Scripted parameters are a way to incorporate a Python or Tcl script into the generation of a parameter value.

This script can include references to other user parameters, meaning one parameter value can be calculated based on the value of another. Parameters referred to in the scripts are generally published parameters that accept input from the user.

So, user input can be accepted from one parameter, and this input processed using a script, in order to produce the actual information required by the workspace.

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 3C </span>
</td>
<td style="border: 2px solid darkorange;background-color:darkorange;color:white">
<span style="color:white;font-size:x-large;font-weight: bold">Data
Download
Parameters</span>
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
<td style="border: 1px solid darkorange">Improve
the
data
download
service</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Demonstrates</td>
<td style="border: 1px solid darkorange">Providing
User
Parameters
in
a
Data
Download
service</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise3c-­‐Begin-­‐
DataDownload.fmw</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise3c-­‐Complete-­‐
DataDownload.fmw</td>
</tr>

</table>

The Data Download system from Exercise 3b works, but could be improved upon. In particular, it would be helpful for users to be able to choose the resolution and compression of the imagery they are downloading.

**1. Create a Published Parameter for Resolution**

Start FME Workbench (if necessary). Open the workspace from Exercise 3b (or the start workspace for this exercise).

Locate the User Parameters section of the Navigator window. Right-click on the header for this section and choose Add Parameter.

This opens the Add/Edit User Parameter dialog. In this dialog enter the following values:

Type Integer

Name Resolution

Published Yes (Checked)

Optional No (Unchecked)

Prompt Image Resolution (1-50)

Default Value 5