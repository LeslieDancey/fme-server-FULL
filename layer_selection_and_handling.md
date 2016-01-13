# Layer Selection and Handling

Layer (Feature Type) flexibility can be achieved through the Feature Types to Read parameter.

There is no single method by which users might wish to select data or features. Every organization implementing FME Server lets users select data in different ways.

However, spatial data is often organized in layers (groups, classes, categories, feature types) and a common way that users will wish to choose data is on a layer-basis.

**Selecting Layers**

Allowing users to select data by layer is the simplest solution available in an FME Workspace, although in many situations users will wish to select data not just by layer, but by a mix of criteria.

Allowing choice by layer alone can be handled easily if the layers correspond to Feature Types in the source data.

Each reader in FME has a parameter called Feature Types to Read. When this parameter is published, the workspace will accept a list of layers to read from the user.

The publishing dialog for Feature Types to Read is different because FME can automatically scan the workspace and provide a list of available feature types.

Additionally, the Use Alternate Display Name allows the author to publish alternate names (for example Road Centrelines instead of RdCtrLns) in a similar way to the “Choice with Alias” parameter.

**Grouped Layers**

On some occasions the user does not need to be presented with a full list of layers. Instead they might need to see “groups” of layers.

For example, what is presented to the end-user as “Water” features may actually be made up of multiple source feature types such as Lakes, Rivers, and Streams.

This type of scenario can be achieved using a parameter of type “Choice with Alias (Multiple)”.

Here the author has eight feature types, but wishes to present them to the end-user as three groups of layers.

The first step is to create a parameter of type “Choice with Alias (Multiple)”:

In the parameter configuration, all feature types from the same group are given the same display name:

Finally, the Feature Types to Read parameter is linked to the newly created Choice with Alias parameter:

Now when the workspace is run, the end-user is presented with a set of three options (Environment, Buildings, and Amenities) that reflect a series of different layers/feature types.

<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 3E </span>
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
<td style="border: 1px solid darkorange">The
Feature
Types
to
Read
parameter
for
layer
selection</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise3e-­‐Begin-­‐
DataDownload.fmw</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">C:\FMEData2015\Workspaces\ServerAuthoring\Exercise3e-­‐Complete-­‐
DataDownload.fmw</td>
</tr>

</table>

The task here is to update the current data download service to deliver a hybrid image of aerial photo and map data. We’ll do this by adding a vector data Reader to the workspace and burning (stamping) it into the raster.

**1. Start Workbench**

Start FME Workbench (if necessary). Open the workspace from Exercise 3d (or the start workspace for this exercise).

Select Readers > Add Reader from the menubar and add a new Reader for some roads data with the following parameters:

Reader Format Bentley MicroStation Design (V8)

Reader Dataset C:\FMEData2015\Data\Transportation\RoadsDGN.dgn

Workflow Options Single Merged Feature Type

Click Parameters to open the parameters dialog.

In the dialog check Group Elements by Level Names and click OK. This will ensure data is added with the correct level names (not numbers).

Click OK again to add the Reader. You will see a single source feature type which will allow any layer to pass through.