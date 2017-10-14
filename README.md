# Autospinstaller for sharepoint foundation 2013 or sp1 version

Guide
AutoSPInstaller is a PowerShell based tool which automates the deployment of SharePoint Foundation 2013. It has the ability to granularly configure most aspects of the farm and includes some interesting features such as: centralized farm deployment, granular database naming, XML configuration and more. 

The goal of AutoSPInstaller Online is to simplify this process. It will assist you with all of the configuration including some of the more complicated configurations such as adding additional Web Applications or Site Collections. Furthermore, there is a large amount of code just to make sure that all of the data is valid. 

How to:
Create the following domain accounts (They can be named anything):
SP_Farm (Farm Account)
SP_CacheSuperUser (Object Caching Account)
SP_CacheSuperReader (Object Caching Account)
SP_Services (Service Application Account)
SP_PortalAppPool (Portal Application Pool Account)
SP_ProfilesAppPool (MySites Application Pool Account)
SP_SearchService (Search Service Application Pool Account)
SP_SearchContent (Search Content Access Account)
SP_ProfileSync (User Profile Sync Account)
Requires Replicate Directory Changes Active Directory permission on the domain with which you'll synchronize
Optionally for Enterprise Service Applications (Can be a single account)
SP_ExcelUser (Excel Unattended ID)
SP_VisioUser (Visio Unattended ID)
SP_PerfPointUser (Performance Point Unattended ID)
Download the latest version of the AutoSPInstaller Scripts Here
Assuming that we are going to use this on SharePoint 2010 and that all of your SharePoint servers have Internet access
There is more work required to place all the files in the correct locations if there is no internet access
Please Note: The process is almost identical for SharePoint 2013
Disable Windows Firewall or allow the following ports through the firewall, 22233,22234,22235 and 22236.
Causes issues with Distributed Cache
I would recommend enabling the "Auto Admin Login" option as 2013 requires a number of reboots
Make sure that all the Web Applications use Claims Based Authentication as Classic Based Authentication is now obsolete
Extract the contents of the AutoSPinstaller.zip anywhere ie D:\Temp\
Place the contents of the SharePoint ISO in D:\Temp\SP\2010\SharePoint\
At this point you should have a folder structure similar to this
\SP\2010\
ForeFront (Optional)
LanguagePacks (Optional)
OfficeWebApps (Optional)
PDF (Optional)
SharePoint (Place the SP2010 binaries here)
Updates (Place any Cumulative Updates here, do not slip stream updates anymore as the process is broken!)
SP\2013\
ForeFront (Optional)
LanguagePacks (Optional)
PDF (Optional)
SharePoint (Place the SP2013 binaries here)
Updates (Place any Cumulative Updates here, do not slip stream updates anymore as the process is broken!)
SP\AutoSPInstaller
AutoSPInstallerConfigureRemoteTarget.ps1
AutoSPInstallerFolderStructure.txt (Explains the folder structure further)
AutoSPInstallerFunctions.ps1
AutoSPInstallerFunctionsCustom.ps1
AutoSPInstallerInput.xml (Example XML Configuration, do not edit this one. Leave it for reference)
AutoSPInstallerLaunch.bat (Drag and Drop the XML configuration into this file to start the installation)
AutoSPInstallerMain.ps1
Please Note: You can keep both SharePoint versions binaries in the directories. The XML specifies which version will be installed.

Configuration
At this point we can begin configuring AutoSPInstaller using AutoSPInstaller Online
Please Note: The site has only been tested with the latest versions of each browser, Chrome, FireFox, IE11 and Safari.
Browse back to the Home page, then select either "Load Default Template" or "Load from my XML" if you already have an existing configuration
Navigate through the Farm Options on the left hand side navigation and complete each section
To Save the Configuration
Browse to the "Review & Download" Section and copy all of the text and save it to your machine as .xml (For example FarmA.xml)
Please Note: Spaces in the file name are not supported!

Installation
Copy the SP directory (which we set up above) to all of the SharePoint Servers
Optionally, the installation can be ran from a File Share
Make sure that the logged on user has Local Admin on all the SharePoint Servers and SQL Permissions dbcreate and securityadmin
Browse to the AutoSPInstaller dir ie D:\Temp\SP\AutoSPInstaller
On each SharePoint Server (One at the time):
Drag the new XML file ie FarmA.xml into the AutoSPInstaller.bat

Please Note: If you double click on AutoSPInstaller.bat, it will use the AutoSPInstallerInput.xml config file by default
AutoSPInstaller will now run, it will create a file on the Desktop which will contain the output of the PowerShell window and any errors

If you have any questions please leave a comment.

Enjoy!
