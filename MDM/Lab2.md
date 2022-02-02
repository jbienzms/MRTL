
![](Images/MRTL-MDMBanner.png)

# Welcome to the Mixed Reality MDM Track. 

## Lab 2: Import Wi-Fi settings for HoloLens devices in Intune
For more information see [Import Wi-Fi settings for Windows devices in Microsoft Intune | Microsoft Docs](https://docs.microsoft.com/en-us/mem/intune/configuration/wi-fi-settings-import-windows-8-1#export-wi-fi-settings-from-a-windows-device)  

Intune will accept an export of an existing Wi-Fi profile in the form of an XML file.  
The next instructions should be carried out on a Windows PC rather than a HoloLens or in Intune. 


### Export Wi-Fi Settings from a Windows Device

1)	Create a local folder for the exported Wi-Fi profiles such as “c:\wifi”.
2)	From the start menu, navigate to “Command Prompt” and right click to select “Run as Administrator”.
 ![](Images/lab21.png)    

  

![](Images/lab22.png)  
 

3)	Once the Command Prompt window is open type run the following command, “netsh wlan show profiles”.   
a.	It is important that you then write down the name of the Wi-Fi profile you are currently connected to and that you intend to export. Your screen will appear as below with your profiles
![](Images/lab23.png)


 

4)	In the command prompt then enter “netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi” where the ProfileName is the name of the wifi profile you previous had written down  
![](Images/lab24.png)  


 

5)	The WiFi profile will now be created and added to the C:/Wifi folder in the format Wi-Fi-ProfileName.xml

### Import the Wi-FI settings into Intune

1)	Go to the Microsoft Endpoint Manager Admin Center  https://endpoint.microsoft.com/ and sign in.
 
 ![](Images/lab25.png)

Figure 1 - Microsoft Endpoint Manager Admin Center  
	

2)	Go to Devices  Configuration profiles  Create Profile  
 ![](Images/lab26.png)  

Figure 2 - Devices/Configuration Profile - Create Profile  

3)	When creating a profile,  set the following properties, then Select “Create”.  

| Property | Value |   
| --- | --- |
| Platform | Windows 8.1 and later| 
| Profile | Wi-Fi Import |

![](Images/lab27.png)  
 
Figure 3 - Devices/Configuration profile - Create a profile – Profile type: Wifi Import 


4)	For the basics, give the profile a name “Wi-Fi Import” and add a description to help distinguish its purpose e.g. “Imported Wi-Fi profile for Windows Holographic devices”. Select Next.  
 ![](Images/lab28.png)

Figure 4 - Configuration Profile/Wi-Fi Import - Basics  

5)	For the configuration settings, provide a Wi-Fi Connection name, this can be the name of our Wi-Fi connection or a name of your choosing. As an example, enter LabWiFi. 

For the Profile XML, use the folder icon to navigate to the exported Wi-Fi profile located in the C:/wifi folder (See step 5 of the Export Wi-Fi Settings from a Windows Device section). 

The .xml file created previously in the earlier step will be uploaded here and be displayed read only in the editor. Select the file, Open the file. When the XML is populated in the editor, select Next. 
 
![](Images/lab29.png)

Figure 5 - Profile XML - uploading the Wi-Fi Profile XML file  
![](Images/lab30.png)

 
Figure 6 - XML file uploaded and displayed in the read only editor  
6)	In Assignments, select the users and groups you would like to apply the profile to. In this scenario, Click “Add Groups” to apply to the group we created in the pre-requisite steps, select “HoloLens Autopilot Devices” then click Select. Select Next.  

*Note: You can equally exclude certain groups from receiving this Wi-Fi import but for the purpose of this example we will not be excluding any groups.*  

![](Images/lab31.png)

Figure 7 - Assigning groups to the WiFi import configuration profile
 ![](Images/lab32.png)

Figure 8 - Selected HoloLens Autopilot Devices group to be assigned
 ![](Images/lab33.png)

Figure 9 - Profile assigned to the desired group  

7)	Complete the final review of the configuration profile and Select “Create”.
 ![](Images/lab34.png)

Figure 10 - Wifi configuration profile – summary – Review + Create  

The profile is created and assigned. Feel free to assign this profile to further groups and users in the future.

*Note: When you validate the Wi-fi profile by apply to an autopilot policy and running on the device there will be a remediation error which is expected and the correct result* [See Here for More Info](https://docs.microsoft.com/en-us/mem/intune/configuration/wi-fi-settings-import-windows-8-1#export-wi-fi-settings-from-a-windows-device)