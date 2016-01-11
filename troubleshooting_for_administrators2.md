# Troubleshooting for Administrators

This section shows a few basic troubleshooting techniques in case of emergency

**FME Workbench-FME Server Connection**

If you are unable to connect from FME Workbench to FME Server then the following suggestions may be of help.

• Check if there is a firewall running on either your computer or the FME Server. If so, you must open port 7071 to use Direct Connection or port 80 (or 8080) to use the Web Connection.

• Restart the FME Server Services. On Windows, go to Start > Programs > FME Server > Windows Service > right-click Restart and select Run as administrator.

**Workspaces are Queued but not Run **

If a workspace appears in the FME Server queue, but is never executed, then it may be because no engines are running.

• Check the Web User Interface (Manage > Engine Management) to confirm engine status.
If no engines are available check licensing and update as necessary. Restart FME Server once a proper licence is in place.