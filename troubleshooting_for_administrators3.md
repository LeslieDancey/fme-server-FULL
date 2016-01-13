# Troubleshooting for Administrators

This section shows a few basic troubleshooting techniques in case of emergency

**Data Download: No Output**

If no zip file is output at the end of a Data Download process then the following suggestions may be of help.

• Run the workspace on FME Desktop to confirm that it does actually write some data. If
there is no output data then no zip file will be delivered.

• Check that the FME Server has access to the source data. If the source data is not available to FME Server then there will be no output.

• On FME Server check the log file using Jobs > Completed to confirm that the process did actually try to write some data. If not an error message may help to indicate why.

**Data Download: Empty Output**

If an empty zip file is output at the end of a Data Download process then the following may be of help.

• Ensure that when you publish the workspace to FME Server you check the Data Download parameters and choose an output dataset to be associated with the Service. If you don’t, then FME has no way to determine which Writer will provide the output.

**Data Streaming: Zipped Output**

If the Data Streaming service does not provide a dataset, but a zip file, then the following may be of help.

• If the output format is one composed of a number of files – for example Esri Shape – then the Data Streaming service will create a zip of the output.

Often raster Writers will write an additional world file, and vector Writers a prj file, in order to preserve coordinate system information, and this can unexpectedly cause this issue. In most cases wld/prj file creation can be turned off with either Writer or Feature Type parameters.