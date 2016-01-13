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