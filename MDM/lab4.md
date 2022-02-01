
![](Images/MRTL-MDMBanner.png)

# Welcome to the Mixed Reality MDM Track. 

## Lab 4: Implementing settings with CSP's


In Windows 10, Configuration Service Providers (CSP)s are an interface to read, set, modify, or delete configuration settings on the device.

Find the full list of HoloLens CSPs [here](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#csps-supported-in-hololens-devices)

Within this guide we will attempt to implement a few different settings

•	Policy CSP - DeviceLock/MaxDevicePasswordFailedAttempts  
•	Tenant Lockdown CSP  

1)	Go to Microsoft Endpoint Manager Admin Center. (endpoint.microsoft.com)

![](Images/Lab41.png)   
Figure 1 - Microsoft Endpoint Manager Admin Center  

2)	Navigate to the “Devices” blade, then to “Configuration profiles”  

![](Images/Lab42.png)    
Figure 2 - Devices blade  


### Create a configuration profile using the custom template to configure CSPs

#### MSFT Tenant Lockdown CSP  

3)	Click “Create Profile”, set the following properties and Click Create:-  

|Platform| 	Windows 10 and later|
| --- | ---| 
|Profile type|	Templates|
|Template name|	Custom| 


Using the custom template we can configure a number of settings each of our CSPs in the list provided at the beginning of the document. 

![](Images/Lab43.png)   
Figure 3 - Devices/Configuration profiles

 ![](Images/Lab44.png)    
Figure 4 - Devices/Configuration profiles/Create a profile - Custom  

The following steps can be used for all the CSPs managed in this way. 

4)	Using the Custom template, in the basics pane input the following, then click Next :-  

|Name|	Tenant Lockdown CSP|
| --- | ---| 
|Description|	Locks a device to a tenant, and ensures that the device remains bound to the tenant in case of accidental or intentional resets or wipes.|


![](Images/Lab45.png)    
 
Figure 5 - Custom template – Basics  (Tenant Lockdown CSP)  


5)	In Configuration settings, click Add. 

![](Images/Lab46.png)     
Figure 6 – Custom template - Configuration settings  


6)	In the Add Row pane, use the following table to input the fields :-  

|Name|	Tenant Lockdown|
| --- | ---| 
|Description|	-|
|OMA-URI|	./Vendor/MSFT/TenantLockdown/RequireNetworkInOOBE|
|Data Type|	Boolean|
|Value|	True|

Then click Save. 
 ![](Images/Lab47.png)    
Figure 7 - Custom template, Add Row, OMA-URI Settings

7)	Review the configuration settings, that have been added to this profile. If they are correct click Next.
Note: When implementing for a customer multiple settings can be added here.  
 
![](Images/Lab48.png)    

 
Figure 8 - Custom template, Configuration settings summary  

8)	In Assignments, click Add groups. On the Select groups to include pane, select the HoloLens Autopilot Devices group and then click Select.  
![](Images/Lab49.png)    
Figure 9 - Custom - Assignments - HoloLens Autopilot Devices  


9)	Review the added group under Included groups. Click Next.

![](Images/Lab410.png)     
Figure 10 - Custom - Assignments review groups  



10)	Skip the Applicability Rules pane. Click Next.   

*Note: If wanted to only apply these settings to a subset of devices you could create a Rule with specific properties in this pane.*

 ![](Images/Lab411.png)   
Figure 11 - Custom - Applicability Rules  


11)	Review the Custom profile settings and if correct click Create.  
![](Images/Lab412.png)  
 
Figure 12 - Custom - Review + create

#### Policy CSP – Device Lock – Max Device Password Failed Attempts
Link to CSP - DeviceLock/MaxDevicePasswordFailedAttempts

12)	Click “Create Profile”, set the following properties and Click Create:-  

|Platform|	Windows 10 and later|
| ---|---|
|Profile type|	Templates|
|Template name|	Custom|

Using the custom template we can configure a number of CSPs that can be used together, independently and with a number of devices.  

![](Images/Lab413.png)    
Figure 13 - Devices/Configuration profiles  


![](Images/Lab414.png)     
Figure 14 - Devices/Configuration profiles/Create a profile – Custom


13)	Using the Custom template, in the basics pane input the following, then click Next :-  

|Name|	Max Device Password Failed Attempts|
| --- | ---| 
|Description|	The number of authentication failures allowed before the device will be wiped. A value of 0 disables device wipe functionality.|

 ![](Images/Lab415.png)    
Figure 15 - Custom template – Basics  (Max Device Password Failed Attempts)  

14)	In Configuration settings, click Add.  

![](Images/Lab416.png)     
Figure 16 – Custom template - Configuration settings  

15)	In the Add Row pane, use the following table to input the fields :-  

|Name	|Max Device Password Failed Attempts|
|---|---|
|Description|	-|
|OMA-URI|	./Vendor/MSFT/Policy/Config/DeviceLock/MaxDevicePasswordFailedAttempts|
|Data Type|	Integer|
|Value	|4|

Then click Save. 

NOTE: For Policy CSPs we follow the format to configure the policy :- 

•	./Vendor/MSFT/Policy/Config/AreaName/PolicyName 

In the example above AreaName = “DeviceLock” and PolicyName = “MaxDevicePasswordFailedAttempts”.


 ![](Images/Lab517.png)  
Figure 17 - Custom template, Add Row, OMA-URI Settings  


16)	Review the configuration settings, that have been added to this profile. If they are correct click Next.
Note: When implementing for a customer multiple settings can be added here.  

![](Images/Lab518.png)    	 
Figure 18 - Custom - Max Device Password Failed – summary  


17)	In Assignments, click Add groups. On the Select groups to include pane, select the HoloLens Autopilot Devices group and then click Select.  

![](Images/Lab519.png)    
	 
Figure 19 - Custom - Assignments - HoloLens Autopilot Devices  


18)	Review the added group under Included groups. Click Next.

![](Images/Lab520.png)     
Figure 20 - Custom - Assignments review groups  
 

19)	Skip the Applicability Rules pane. Click Next.  

*Note: If wanted to only apply these settings to a subset of devices you could create a Rule with specific properties in this pane.*

 ![](Images/Lab521.png)    
Figure 21 - Custom - Applicability Rules  

 
20)	Review the Custom profile settings and if correct click Create.

![](Images/Lab522.png)   
Figure 22 - Custom - Review + create

