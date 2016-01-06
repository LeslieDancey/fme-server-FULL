# Running a Workspace on FME Server

This section introduces running a workspace on FME Server

Once a workspace is uploaded to FME Server, it can be run on that server. There are several ways to run a workspace, the simplest being using the Job Submitter service.
This service can be accessed either through the Web User Interface or via a URL

Running the Job Submitter using the Web Interface Using the web interface to run a workspace is very similar to running it in FME Workbench; you simply locate the workspace and click a Run button.

To locate a workspace first click on Workspaces or the Run Workspace entry in the main menu of the web interface.

Secondly, click on the repository that contains the workspace to be run.

Next, click on the workspace itself.

Finally you have the option to click which service to configure or run.

**Configuring a Translation**

Clicking on a service for a workspace is the equivalent to the Prompt and Run option in FME Workbench. You get to define what parameters are going to be set for the translation, such as File to Upload, Source File and Output Coordinate System.

For example, here the user can specify where the source data is available:

If data was made available using Resources functionality, then the user could choose the Browse option to search for and select it:

Once the parameters are set, click the Run Workspace button to complete the process.