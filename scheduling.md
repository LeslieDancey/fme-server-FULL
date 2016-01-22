# Scheduling

Scheduled Translations are the best way to kick off a workspace at a particular time or date

**What is Scheduling?**

Scheduling is the ability to program FME Server to run a workspace in a repository, at a specific time in the future. The schedule can cause the workspace to run once or on a repeating basis.

**Managing Scheduled Tasks**

Scheduled tasks are set up in a the Web User Interface. Apart from a quick link on the main page for adding a scheduled task, there is a section under the Manage menu:

The interface supports all the capabilities you would expect, including the ability to create, delete, copy, enable and disable scheduled tasks:

**Creating a Scheduled Task**

There are a number of parameters involved in creating a scheduled task.

The first parameters are very simple ones for naming and describing the schedule.

Notice that each schedule can be assigned to a particular category.

There is also a parameter for deciding whether the schedule will be enabled straight away.

The next few parameters concentrate on the workspace to be run.

Once a workspace is selected there will be a short pause while FME retrieves information about the workspace. It will then expose any published parameters that exist in the workspace:

The key parameters, of course, are for setting the actual schedule. Here the workspace is set to run every week starting on the 27th February at 2:00am

There are also optional parameters for notification topics to trigger on completion of the scheduled task. These could be used to inform an administrator of the success or failure of the translation.

Finally there are options to control job priority, job routing (which engine it should use) and job expiry (for jobs that are time-sensitive and would be no longer useful if held back past a certain time by higher priority tasks).

Once the parameters are set for a scheduled task, it is added to the main Scheduling interface.

Notice that there are a number of pre-defined jobs, automatically installed with FME Server for the purpose of backing-up and maintaining various components.


<table style="border-spacing: 0px;border-collapse: collapse;font-family:serif">
<tr>
<td style="vertical-align:middle;background-color:darkorange;border: 2px solid darkorange">
<i class="fa fa-cogs fa-lg fa-pull-left fa-fw" style="color:white;padding-right: 12px;vertical-align:text-top"></i>
<span style="color:white;font-size:x-large;font-weight: bold">Exercise 5A </span>
</td>
<td style="border: 2px solid darkorange;background-color:darkorange;color:white">
<span style="color:white;font-size:x-large;font-weight: bold">Scheduling</span>
</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Scenario</td>
<td style="border: 1px solid darkorange">City of Austin</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Data</td>
<td style="border: 1px solid darkorange">Apartment Data</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Overall Goal</td>
<td style="border: 1px solid darkorange">Web
Map
Application
with
WebSockets</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Demonstrates</td>
<td style="border: 1px solid darkorange">Automated
Scheduling</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Starting Workspace</td>
<td style="border: 1px solid darkorange">n/a</td>
</tr>

<tr>
<td style="border: 1px solid darkorange; font-weight: bold">Finished Workspace</td>
<td style="border: 1px solid darkorange">n/a</td>
</tr>

</table>

This is a simple exercise to schedule a workspace to translate data.

**1. Open Web User Interface**

Open the FME Server Web User Interface and log in.

**2. Select Schedules**

Select Schedule Workspace from the homepage.

**3. Create Schedule**

Click New on the schedules menu to start creating a new schedule.

Enter a name for the schedule (something like ApartmentSchedule) and enter a name for a new category (like MySchedules)

For the workspace to execute select the repository called Samples and in there select the workspace austinApartments.fmw