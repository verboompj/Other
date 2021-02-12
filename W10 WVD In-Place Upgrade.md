# UNSUPPORTED 

## Unsupported

Upgrading Persistent Desktops is something that is inevitable in time. 
As Feature updates are released on a ~6 month cadence , it makes sense to move from your 1903 release (19H1) to a say 2004 ( 20H1 ) in some point in time, as they will run out of support at some stage. 

WVD currently offers no solution for it, and technically Azure does not support in-place upgrades of the OS:
https://docs.microsoft.com/en-us/troubleshoot/azure/virtual-machines/in-place-system-upgrade 

Its the Cat vs Kettle discussion.
Also, in any VDI solution, sucessfully seperating the Apps, Profile and OS mitigates this scenario and allow for the OS to be replaced rather then to be upgraded.
One would be able to replace the OS and leave Apps ( MSIX App Attach ) and Profile ( FSLogix ) untouched.

Now thats only true for a number of cases, and is completely true for Pooled, non-persistent desktops of course. 
But in case we have dedicated, pweronal desktops that have heavy modifications applied by the end-user things get complicated.

As an unsupported route, some customers are succesfull in replacing the OS in-place on Azure.
The thing that cathes most deployments is the lack of console access;  where normally one would accept the EULA and enroll the OOBE experience at the initial launch of a fresh Windows 10 deployment. Since this is unavailable for Azure VM's, we need to navigate around the OOBE (Out Of Box Experience). 
A way to force this is by running the setup command and adding the 'showoobe none'  command.

'setup.exe /auto upgrade /migratedrivers all /dynamicupdate enable  /compat ignorewarning /showoobe none'

