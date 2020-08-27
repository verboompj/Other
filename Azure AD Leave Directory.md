# Leave a Azure Active Directory / Tenant your Azure AD Account was added to as a Guest account

Sometimes it makes sense to be added as a guest to an external Azure Active Directory. In this way, you can use your own Azure AD Account to get access to external resources, without the need for the other party to setup and maintain an account for you.

After completion of my task, most of the times I noticed that, although my permissions were removed, my account would still be registered as a guest account in the other parties Azure Active Directory. This was building up to quite a list of "Directories" I could choose from when logging on to services like the Azure Portal.

I found out I can remove myself from the other parties Directory using the Azure AD Account Portal https://account.activedirectory.windowsazure.com/r/#/profile 
At the bottom of the screen you see a list of Directories your account is added to. 

----------------

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/Capture2.PNG)

-----------------

By signing in to the tenant you'd like to leave, and then clicking the "BacK" button of your browser twice, you see the option to now remove yourself from that particular tenant by clicking the `Leave Organisation` link:

----------------

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/Capture3.PNG)

-----------------

