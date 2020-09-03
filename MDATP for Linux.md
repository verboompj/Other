# WDATP & Security Center for OnPremises Linux Servers


I gave WDATP for Linux a spin. In a small environment a maunal setup is a 20 min process.
I've enrolled 2 OnPremises Ubuntu machines running Docker, and wanted the machines to be available in Azure Security Center as well as in the WDATP Portal. 

All in all fairly straight forward: Ubuntu 20.04 Server(S) enrolled in MDATP and Azure Security Center : 

----------------
### WDATP:

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
