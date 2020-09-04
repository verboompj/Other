# MDATP & Security Center for OnPremises Linux Servers


I gave MDATP for Linux a spin. In a small environment a maunal setup is a ~10 min process if you have a tenant setup and have MDATP Portal access.
If you don't , you can enable MDATP on a existing Tenant by adding Trial licenses for M365 E5.

I've enrolled 2 OnPremises Ubuntu machines running Docker, and wanted the machines to be available in Azure Security Center as well as in the MDATP Portal. 

All in all fairly straight forward: Ubuntu 20.04 Server(S) enrolled in MDATP and Azure Security Center : 

----------------
### MDATP:

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/wdatpdevices.PNG)

-----------------
## ASC: 

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/securitycenter.PNG)

-----------------

## Steps & Catches: 

#### Repo setup
I followed the following steps on this Doc: https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/linux-install-manually 

Mind the Version and Channel you need to add in steps 3 and 4 of the repository setup:
`curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list`

#### Client Onboarding Package
Downloading the Onboarding Package i did manually by copying the content of the `MicrosoftDefenderATPOnboardingLinuxServer.py` over manually from a browser to my CLI.
Creating a new file in Downloads\MicrosoftDefenderATPOnboardingLinuxServer.py 

So you can skip to the Client Configuration section

#### Test 

make sure you download the EICAR (test) File : curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt

#### Verify

My nodes popped up nicely in the MDATP Portal : https://securitycenter.microsoft.com 

## Azure Security Center (ASC) steps:

Pretty straigt forward actually , browsing to ASC in the Azure portal, clicking Compute and then Add Servers:

![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/ascadd1.PNG)



Selecting the right ( Security Center enabled ) Workspace. I chose to combine my Security Center Workspace with my existing Azure Monitor Log Analytics workspace


![Screenshot](https://github.com/verboompj/Other/blob/master/Pictures/ascadd.PNG)

And thats it. You'll see the nodes apearing in ASC in a couple of minutes.



