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