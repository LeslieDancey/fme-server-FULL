# Geographic Selection

In most Self-Serve applications the user will need to be given a choice of geographic area of interest

Although most workspaces are designed around FME feature types, this may not be how the end-users see the data, or how they need to select it. An installation that provided selection only by layer (or even a group of layers) would be very limiting indeed.

Besides layers, other methods of data selection revolve around spatially defining an area of interest. There are three obvious ways of doing so:

- A simple, rectangular bounding box

- An existing area such as a regional or municipal boundary

- An ad-hoc area (one drawn by the user on the fly)

**Bounding Box**

A bounding box can be defined in several ways, but the easiest is to use a set of parameters.

All FME readers have parameters to define the bounding box (envelope) of data that is being read. This is the most efficient method of selecting an area of interest because it means FME does not have to read the entire dataset first and then clip it to size; it can read only what data is necessary. It’s particularly efficient if the source format has a spatial index, and it applies to both vector and raster datasets.

If these search envelope parameters are published, then the end-user is able to enter values that define the extent of the data he/she is interested in.

Besides the actual coordinates, there are two related parameters: “Clip to Search Envelope” and “Search Envelope Coordinate System”.

Clip to Search Envelope causes features that overlap the bounding box to be clipped and the outer part discarded. This will be the most common use for FME Server.

The Search Envelope Coordinate System means that the bounding box can have its own coordinate system, separate from the reader coordinate system. So the bounding box coordinates can be defined in a general coordinate system like Lat./Long, even if the data is UTM.

**Web Mapping and Bounding Boxes**

Bounding box parameters are particularly useful when a web mapping application (for example Google Earth) is requesting data. The application will provide the extents of the current map view and the workspace restricts itself to reading features within those extents.

This, of course, is done using published parameters. The parameters in the workspace need to be given specific names when published, as follows:

• bboxWest

• bboxEast

• bboxNorth

• bboxSouth

If given these names, both OGC services and the KML Network Link service can make use of these parameters. In fact, if you have used an OGC web service, or a KML Network Link service (as below), you might have noticed how these are used to pass information back to the workspace:

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Ms. Analyst says…</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
“Using reader parameters like this ensures the data is reduced in size at
the earliest possible opportunity and so gives a better performance.”
</span>
</td>
</tr>
</table>

**Irregular Areas of Interest**

An irregularly shaped area cannot be used as a clip boundary in a Reader’s parameters.
However, it can be used to clip data using either a Clipper transformer or a FeatureReader transformer.

The Clipper has an input port for the area of interest (Clipper) and one for the main dataset (Clippee).

For example, here the portal will deliver only addresses that fall inside the boundary of the city of Vancouver:

Here is the same result but using a FeatureReader transformer.

The FeatureReader reads the main dataset directly, executing out one of any number of spatial filters.

In general the FeatureReader is a better choice than a Clipper when using a database with a spatial index, or when the spatial predicate is other than a simple CONTAINS function.

**Existing Area of Interest**

The main issue with an irregular area of interest is how to define that area. In some cases, the feature is already defined as a known shape, such as an administrative or municipal boundary, and already exists in a spatial dataset.

In that case the area can simply be read from the dataset and routed into the appropriate input port of the Clipper/FeatureReader transformer.

If the source contains a number of features, then a published parameter can be used for the enduser to identify the area they want and for FME to filter other features out.

For example, this Self-Serve workspace uses a Clipper transformer to deliver only addresses that fall within a chosen postal code. The postal code is selected by the user through a published parameter. The Tester transformer filters out postal code boundaries that don’t match the user’s selection.

**Ad Hoc Area of Interest**

In the case that the area of interest is not a previously known shape – for example it is one defined entirely by the end user – then a different technique is needed.

This scenario needs a published parameter through which a geometry string can be provided.
The geometry could be, for example, either WKT (Well-Known Text) or XML.

One simple method would be to use an AttributeCreator transformer and publish the Value part.

This could be used in a sequence like this, where the translation is triggered with a Creator, the geometry string retrieved with the AttributeCreator, the attribute contents converted into true geometry with a GeometryReplacer, and then the real data read with a FeatureReader:

To use XML you could also just publish the geometry parameter in a Creator transformer.

With these methods, a web mapping interface that allows the user to define their own custom area of interest can pass it to the FME workspace to be used as the area of interest in a Clipper or FeatureReader.