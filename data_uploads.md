# Data Uploads

Data Upload is a good way for a user to provide data to be
processed

**What is Data Upload?**

As the name suggests, Data Upload allows a user to deliver data to FME Server for processing.

Data Upload can be used from any FME Server client, including:

• The Web User Interface
• An FME workspace
• A custom web application

Data Upload is often used for submitting data to an organization, for example a property developer submits a planning application containing a DWG dataset to a municipal planning department.

It is also often used for publishing data to be processed on FME Server, for example where FME Server is set up as a data validation web service and an end-user is uploading a set of data to be checked.

It’s worth noting that data upload also includes other resources that may be required for a translation to run; for example custom transformers or text-file lookup tables may also be uploaded.

**Implementing Data Upload**

In FME, there are two forms of data upload: the Data Upload Service and the Resource Folders.

The Data Upload Service allows data to be uploaded to a particular workspace in a particular repository. The data is held temporarily for the workspace to be run.

The Resource Folders allow data to be uploaded to a folder for use by any workspace in any repository. This upload is persistent and the data held there for as long as it required.

**The Data Upload Service**

The Data Upload Service allows data and other resource files to be uploaded to FME Server.

Files can be uploaded through the FME Server Publishing Wizard, when a workspace is published from Workbench to FME Server:

Clicking the Select Files button opens a dialog that shows what data is being uploaded.

The upload of these files can be turned on and off as required, and you can also change the location to which data is uploaded – either to a repository (Data Upload) or to a Resource Folder – by clicking the Change Location button.

The other way to upload data with this service is through the configure dialog when running a workspace.

Use the File Upload section to upload the data, then choose Select From Recently Uploaded Files to select which files should be assigned to which published parameter:

Be aware that data uploading with this service is only available with the chosen workspace. Also, the data is stored only temporarily and will be deleted in – by default – 30 minutes time.

**Resources Folders**

Resource Folders are a more permanent and flexible way to upload data and resources to FME Server. Similarly to the Data Upload Service, files can be uploaded at the same time as a workspace.

When editing the resource info (in the publishing wizard, under Select Files, Change Location) you would simply choose to upload the files as a shared resource (left). One other requirement is to select a location on the resources file system.

Another way to use this functionality is to use the Resources tool in the FME Server Web User Interface (below). Here you can upload, download, copy, move, and delete files; plus manage folders too.

**Resource Upload**

To upload data simply click on a folder and then choose the Upload option:

The upload tool gives you the option to either upload a set of files, or an entire folder of data:

To upload a folder of data requires use of a browser – for example Google Chrome – that has folder upload capabilities. At the time of writing, neither Firefox nor IE has this ability.

**New Folder**

The New Folder tool creates a new folder or sub-folder in the Resources mechanism.

For example, to create a subfolder in the Data folder simply click on Data and then click

**New Folder:**

You are prompted to enter a name for the new folder.
Enter a name, click OK, and the folder is created.
Besides those methods, folders in the Resources mechanism can be accessed – or created – in the server’s file system.

For example, here are folders in C:\apps\FMEServer on a Windows file system.

**Benefits**

Resource Folders are more permanent because the data is not automatically deleted after a set time. Instead all uploaded files reside there until removed by a user/administrator.

Additionally, Resource Folders are more flexible for a number of reasons.

Firstly, you can access the files and manage them through a file system on the server. This is useful in itself, but it also allows the data to be accessed through UNC paths, which the Data Upload service does not.

Secondly, Resource Folders can be used for more than data upload.

It’s also possible to write the results of a translation to a resource folder, as in this example. You would just set the output dataset parameter to a resource folder.

Also, files inside a Resource Folder can be managed using the REST API too, with POST and GET functions for downloading files, creating folders, and copying files (for example). This gives control over these resources to any developer who wishes to create their own web applications.

