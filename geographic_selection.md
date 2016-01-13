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