# Other Self-Serve Services

Data Download is not the only Self-Serve Service available.

**Data Streaming**

Whereas the Job Submitter service writes data, and the Data Download service returns a link to the data, a Data Streaming service returns a file of the data itself, streamed back to the client.

For example, the URL for the service can be posted into a web browser, and the data will be automatically downloaded and opened in the application associated with that file type.

Alternatively, the URL can be used directly as the source for a client application. When the client actively downloads the contents on a regular basis – as a GeoRSS reader would – then you have a feed, which is significantly different to a regular data download service.

Data Streaming is a slight misnomer in that a data streaming service does not supply a continuous stream of data; it merely provides a snapshot of the data at a particular point in time.

**What Formats can be Streamed?**

You can use any workspace with the data streaming service, provided it writes data in a format that is file-based or folder-based.

If an output dataset is comprised of more than one file, the service automatically creates a compressed (zip) folder out of the data. For example, AutoCAD DWG format could be streamed, whereas ESRI Shape would be returned in a zipped file.

The most popular formats to stream are those that have a suitable client to read the feed.
Some of the main formats that are output using the data streaming services include:

• RSS

• GeoRSS

• GeoJSON

• KML

• HTML

• JSON

**MIME Types in Workspaces**

A MIME header is a component of a file or e-mail message that is capable of indicating the content type of the file; for example, Content-Type: text/plain indicates a simple text file.

The application that opens a streamed file will depend on the MIME type and file association on the client’s system. MIME type is provided in FME by the first Writer added to the workspace.

The only Writers in FME with a MIME type setting are the TextLine (text file) and Data File Writers.

This parameter only appears when the Writer is added, and (for example) it allows the workspace author to set a MIME type of HTML and therefore stream data directly into a web browser.

**KML Network Link**

A KML Network Link service is when the output from an FME Server translation is a simple KMZ (zipped KML) file that contains solely a network link to reference the workspace on the server.

Whenever a KML browser (such as Google Earth) opens this dataset it follows the link, triggering FME Server to run the translation and return the true output data.

Because Google Earth permits a refresh rate for network links, the translation can be re-run at a user-defined interval. This way the results are always as up-to-date as the chosen interval.

Of course, in this scenario the output is never written to a permanent dataset; the resulting data is simply streamed to the browser, which writes it to a cache.

As with other services, a workspace becomes available for use as a KML Network Link service when the author checks the KML Network Link checkbox in the FME Server Publishing Wizard.
The edit button provides a whole series of different parameters that control the refresh rate when the data is opened in Google Earth.