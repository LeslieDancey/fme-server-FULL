# Running Workspaces on FME Server

FME Workbench is the authoring environment for FME Server translations. It has functionality specifically for FME Server.

**FME Desktop as an FME Server Authoring Tool**

FME Server can be called a model-driven architecture, because the specification for a translation is expressed as a model. In FME, these models are better known as **Workspaces**.

Workspaces are created – we call it “authored” – using FME Desktop. In particular, the **FME Workbench** application is used. FME Workbench is a client of FME Server, and so they form a client-server pair. However, both share the same core engine and process data the same way.

**The Workspace Authoring Workflow**

The four basic steps to creating and using a workspace on FME Server are:

• Author the workspace in FME Workbench.
• Publish the workspace from FME Workbench to FME Server.
• Run the workspace on FME Server.
• Maintain the workspace by downloading it from FME Server, making any required updates in FME Workbench, and re-publishing it back to FME Server.

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
“Be aware that FME Workbench is part of the FME Desktop product and is
not included as part of FME Server.”
</span>
</td>
</tr>
</table>