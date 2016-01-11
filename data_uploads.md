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