# UNSUPPORTED BY Microsoft

## Unsupported

Upgrading Persistent Desktops is something that is inevitable in time. WVD currently offers no solution for it, and technically Azure does not support in-place upgrades of the OS. 
https://docs.microsoft.com/en-us/troubleshoot/azure/virtual-machines/in-place-system-upgrade 


Its the Cat vs Kettle discussion.

Sucessfully seperating Apps, Profile and OS mitigates this scenario, where one would be able to replace the OS and leave Apps ( MSIX App Attach) and Profile ( FSLogix ) untouched.



setup.exe /auto upgrade /migratedrivers all /dynamicupdate enable  /compat ignorewarning /showoobe none 
