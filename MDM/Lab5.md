
![](Images/MRTL-MDMBanner.png)

# Welcome to the Mixed Reality MDM Track. 

## Lab 5: Kiosk Mode

In this lab we will set up a single app and multi app kiosk and we will look at the steps that differ between the two.

## Preparation
Before beginning the Kiosk creation piece of this lab we first must set up another Azure AD group. This group will include Azure AD user accounts who will be assigned to the Kiosk experience.

1)	Go to the Azure portal. (portal.azure.com) and log in using your lab credentials. 
 ![](Images/Lab51.png)  
Figure 1 - Azure Portal
 
2)	Click the View button, under the Manage Azure Active Directory section to specifically go the Azure Active Directory.  Go to the Groups Blade
![](Images/Lab52.png)  
 
Figure 2 - Azure Active Directory Portal Overview

3)	In All Groups, select New Group.  
 ![](Images/Lab53.png)  
Figure 3 - Azure AD Groups | All Groups  


4)	On the New Group screen, apply the following selections:-  

|Group Type|	Security|
|---|---|
|Group Name|	HoloLens Lab Users|
|Group Description	|A user group which will be used in the HoloLens demos|
|Azure AD roles can be assigned to the group|	No|
|Membership type|	Assigned|
|Owners|	System Administrator|
|Members|	Alex Wilber, Allen DeYoung, Megan Bowen etc.| 

NOTE: If your custom tenant does not contain pre populated Azure AD user accounts you can follow the steps here to create new accounts to be used as members. 

 ![](Images/Lab54.png)  
Figure 4 - Create a New Group

 ![](Images/Lab55.png)  
Figure 5 - New Group – Security & Name  

5)	Under the Owners field, click “No owners selected” search for the System or Global Administrator account, click the account and Click Select.  
![](Images/Lab56.png)  
 
Figure 6 - New Group - Owner  
 
6)	Under the Members field, click “No Members selected” select some users in the tenant e.g. Alex Wilber, Allen DeYoung, Megan Bowen etc, click the accounts and Click Select.
 ![](Images/Lab57.png)  
Figure 7 - New Group – Members

7)	Review the new group settings and Click Create.  
 ![](Images/Lab58.png)    
Figure 8 - New Group - Final summary

It will take a little while after clicking Create for the Azure AD User Group to appear in Groups| All Groups.

### Microsoft Intune Single App Kiosk with a custom line of business app

1)	Go to Microsoft Endpoint Manager Admin Center. (endpoint.microsoft.com)
 ![](Images/Lab59.png)  
Figure 9 - Microsoft Endpoint Manager Admin Center

2)	Navigate to the “Devices” blade, then to “Configuration profiles”
 ![](Images/Lab510.png)  
Figure 10 - Devices blade
 
3)	Click “Create Profile”, set the following properties and Click Create:-

|Platform|	Windows 10 and later|
| ---| ---| 
|Profile type|	Templates|
|Template name|	Kiosk|

![](Images/Lab511.png)  
 
Figure 11 - Devices/Configuration profiles

![](Images/Lab512.png)  
 
Figure 12 - Devices/Configuration profiles/Create a profile - Kiosk  
 

4)	To set up the Kiosk, we first need to name the Kiosk Profile i.e. “Single App Kiosk”. Add the Description “Single App Kiosk containing the custom line of business app, ExamplesHub” Then click Next.  

![](Images/Lab513.png)   
Figure 13 - Kiosk - Basics  

5)	In Configuration Settings, under Select a kiosk mode select Single app, full screen kiosk and for User logon type select Azure AD user or group (Windows 10, version 1803 and later, or Windows 10, version 1803 and later, or Windows 11). This will trigger further dialogues to make configurations.   

![](Images/Lab514.png)  
 
Figure 14 - Kiosk - Configuration Settings - Select a Kiosk mode

 ![](Images/Lab515.png)  
Figure 15 - User logon type - Azure AD user or group
  
   
6)	To define who the Kiosk experience will be available to click the Add button to select the users and groups to add to the Kiosk. Select any Azure AD user account e.g. System Administrator as the logon for the single app kiosk. Then click Select.  

*NOTE: It is advisable to create a user account to be dedicated to the single app kiosk.*

![](Images/Lab516.png)     
Figure 16  - Azure AD user or group - Select Users or groups  


7)	Make sure that the Logon name reflects the user account you selected.

8)	For Application Type, select Add Store app. Under the App to run in kiosk mode section click Select app which will load the App to run in kiosk mode pane and populate apps that have been uploaded to the store. The app uploaded in lab 3 will be visible here – ExamplesHub. Select this app and click OK.  
![](Images/Lab517.png)    

 
Figure 17 - Kiosk - App to run in Kiosk mode - add custom app  


9)	Having selected the application this should appear in the section App to run in Kiosk mode as seen below. Keep the setting, Specify Maintenance Window for App Restarts to Not Configured. Click Next.  
 

10)	In Assignments, click Add groups. The Select groups to include select the HoloLens Autopilot Devices group. Click Select.  
  ![](Images/Lab518.png)  
Figure 18 - Kiosk - Select groups to include

![](Images/Lab519.png)    

![](Images/Lab520.png)  

Figure 19 - Kiosk - Review Assignments  


11)	 Skip the Applicability Rules pane. Click Next.  

*Note: If wanted to only apply these settings to a subset of devices you could create a Rule with specific properties in this pane.*   



![](Images/Lab521.png)  
 ![](Images/Lab522.png)   

Figure 20 - Kiosk - Applicability Rules

12)	Review the final configuration on the summary page and click Create.  


### Multi App Kiosk with several apps including a custom line of business app


1)	Go to Microsoft Endpoint Manager Admin Center. (endpoint.microsoft.com)
![](Images/Lab523.png)   
Figure 21 - Microsoft Endpoint Manager Admin Center

2)	Navigate to the “Devices” blade, then to “Configuration profiles”
 ![](Images/Lab524.png)  
Figure 22 - Devices blade

  
3)	Click “Create Profile”, set the following properties and Click Create:-  

|Platform|	Windows 10 and later|
| --- | --- | 
|Profile type|	Templates|
|Template name|	Kiosk|

![](Images/Lab525.png)  

 
Figure 23 - Devices/Configuration profiles  
![](Images/Lab526.png)   

 
Figure 24 - Devices/Configuration profiles/Create a profile - Kiosk  


4)	To set up the Kiosk, we first need to name the Kiosk Profile i.e. “Multi App Kiosk”. Add the Description “Multi App Kiosk containing the custom line of business app, ExamplesHub and some in box applications” Then click Next.  

![](Images/Lab527.png)   
 
Figure 25 - Kiosk - Multi App Kiosk – Basics  

5)	In Configuration Settings, apply the following settings:-  

![](Images/Lab528.png)  

|Select a kiosk mode|	Multi app kiosk|
|---|---|
|Target devices running Windows 10/11 in S mode|	No|
|User logon type|	Azure AD user or group (Windows 10, version 1803 and later, or Windows 10, version 1803 and later, or Windows 11)|

Once the user logon type has been selected, click Add. This will trigger further dialogues to make configurations. 

 ![](Images/Lab529.png)    
Figure 26 - Kiosk - Configuration settings - Multi app kiosk  

6)	From the Select users or groups pane, select the HoloLens Lab Users group. Click Select.  
	 
7)	Review the LOGON NAME section to confirm that the correct Azure AD user group has been added.  

8)	Under Browsers and Applications, click Add by AUMID. HoloLens Application User Model IDs (AUMIDs) are used to identify applications and add applications to Kiosks. For a full list of in-box app AUMIDs see [HoloLens kiosk reference information | Microsoft Docs.](https://docs.microsoft.com/en-us/hololens/hololens-kiosk-reference)

Use the following details to fill the Application Names and Application user model ID (AUMID) fields. 

|Application Name	|Application user model (AUMID) for the Win32 app|
| --- | --- |
|Dynamics 365 Remote Assist	|Microsoft.MicrosoftRemoteAssist_8wekyb3d8bbwe!Microsoft.RemoteAssist|
|OneDrive	|microsoft.microsoftskydrive_8wekyb3d8bbwe!App|

After completing the process for Dynamics 365 Remote Assist click OK.

  ![](Images/Lab530.png)   
Figure 27 - Kiosk - Add by AUMID app - Remote Assist (RA)  

  
9)	Repeat step 8 and use the details for OneDrive. Click OK.  
  ![](Images/Lab531.png)   
Figure 28 - Kiosk - Add by AUMID app – OneDrive  

10)	In the same Browsers and Applications section, click Add store app. Select the ExamplesHub app from the populated list, click OK.   

 ![](Images/Lab532.png)   
Figure 29 - Kiosk - Multi app kiosk - Add store app  

11)	Review the 3 apps in the Browsers and Applications section. Make sure that the Autolaunch checkbox for each of these apps is set to No. The tile size should be Medium.  

12)	For the “Use alternative start layout”, “Windows taskbar” and “Allow access to downloads folder”, keep the default selections.

13)	For the “Specify maintenance Window for App Restarts” move the toggle to Require. The Maintenance Window Start Time should be today’s date and set the time to 05:00:00 AM.

14)	For “Maintenace Window Recurrence” leave the default selection of Daily (recommended).
Click Next.

 ![](Images/Lab533.png)  
Figure 30 - Kiosk - Multi app kiosk - Review Configuration Settings    

15)	In Assignments, click Add groups. From the Select groups to include, choose the HoloLens Autopilot Devices group. Click Select.  
  ![](Images/Lab534.png) 

Figure 31 - Kiosk - Multi app kiosk – Assignments  

16)	Review the group that the kiosk will be assigned to and click Next.
  ![](Images/Lab535.png)  

Figure 32 - Kiosk - Multi app kiosk – Assignments review


17)	Skip the Applicability Rules pane. Click Next. 

*Note: If wanted to only apply these settings to a subset of devices you could create a Rule with specific properties in this pane.*
 
  ![](Images/Lab536.png)  

Figure 33 - Kiosk - Multi app kiosk – Applicability Rules


18)	On the Review + Create pane, review the settings of the configuration profile. If correct, click Create.

 ![](Images/Lab537.png)   
 
Figure 34 - Kiosk - Multi App Kiosk - Review Summary part 1

  ![](Images/Lab538.png)   
Figure 35 - Kiosk - Multi App Kiosk - Review Summary part 2


