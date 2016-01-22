# Workflow Management

Workflow Management is great for controlling workspaces in sequence or branching with in-built logic

**What is Workflow Management?**

Workflow Management is a technique where a set of workspaces can be run in a particular sequence, and where branching can take place to run one workspace or another depending on the result of a set of pre-defined decisions.

Workflows like this are set up using a control (parent) workspace, which defines the logic for any decisions that needs to be made, and runs subsequent (child) workspaces according to that logic.

Implementing Workflow Management

A master workspace calls other workspaces by using one of a number of transformers. For FME Server the most commonly used transformer is the FMEServerJobSubmitter.

Here a control workspace is using the FMEServerJobSubmitter to run three further FME workspaces. Maybe each workspace is a separate step in a database update process.

If a particular task fails then the output is routed to a text file Writer – meaning this could be used in a notification system to send an email to an administrator alerting them to the failure.

If there are several workspaces, but only one of which should be run, then the logic for deciding which one can be made using a Tester, or other filter transformer.

For example, here an organization runs a daily process to upload field updates into a database.
However, once a week the process needs to carry out extra actions; such as archiving the source files to Dropbox, or exporting the database contents to Shape files for use by another team.

Each process is defined in a separate workspace, which is called by an FMEServerJobSubmitter transformer.

The Tester transformer prior to the FMEServerJobSubmitters contains the logic over which process is to be carried out. For example it may be testing which day of the week it is. 

If it is Monday to Thursday then the test passes and it will run the usual daily update process. If it is a Friday then the test fails and it will run the weekly update process with the extra tasks.

Again, text file writers are being used to record the result of the translation and whether it was a success or failure. If necessary these could be used to send notifications to a system administrator.

<table style="border-spacing: 0px">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-quote-left fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold;font-family:serif">Monsieur D. Server says…</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange">
<span style="font-family:serif; font-style:italic; font-size:larger">
“The Control Workspace may start with a Reader that reads a
source dataset, where each source feature triggers the job
submitter. For example, the source data may be a list of files that
are to be translated.
But more often just a single feature is needed to trigger the child
process once. In this case a Creator transformer can be used
instead of a Reader.”
</span>
</td>
</tr>
</table>