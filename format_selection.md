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

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 3D </span>
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
<td style="border: 1px solid darkorange">Improve
the
data
download
service</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Demonstrates</td>
<td style="border: 1px solid darkorange">Providing
Coordinate
System
and
Format
Parameters
in
a
Data
Download
service</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise3d-­‐Begin -­‐
DataDownload.fmw</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise3d-­‐Complete -­‐
DataDownload.fmw</td>
</tr>

</table>

The Data Download system from Exercise 3c is still lacking some important user options. Users have asked if they can set the destination coordinate system and data format in the Data Download service.

**1. Start Workbench**

Start FME Workbench (if necessary). Open the workspace from Exercise 3c (or the start workspace for this exercise).

**2. Delete JPEG Writer**

To allow selection of data format we’ll need to remove the existing JPEG format Writer and replace with a Generic Writer.

Locate and click on the JPEG Writer in the Navigator window. Press the delete key to remove it. You will receive a prompt confirming your actions. Click OK to accept the deletion.

**3. Add Generic Writer**

Now the JPEG Writer is removed, we can add a Generic Writer.
Select Writers > Add Writer on the menubar. When prompted enter the following settings:

Format Generic (Any Format)

Dataset C:\FMEData2015\Output\Training

Click the Parameters button to ensure these are set. If no output format is already set then select a format (it doesn’t matter what you choose) and click OK to close the dialog.

Under Add Feature Type(s), ensure Copy from Reader feature type definition is selected.

Click OK again to close the Add Writer dialog.

**4. Edit Feature Type**

When a new Writer is added with Copy from Reader selected, the writer inherits the schema of the specified reader feature type.

Click the cog wheel icon on the Writer feature type to open the properties dialog.

In this dialog uncheck the Dynamic Properties parameter and then type AirphotoMosaic for the Raster File Name.

**5. Connect Feature Type**

In the workspace, connect the new feature type to the RasterMosaicker Output port.