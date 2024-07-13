**Project: Harnessing Advanced Endpoint Management with Microsoft Intune**
--------------------------------------------------------------------------------------
**Hig Level Overview:**

This project will use Microsoft Intune to manage endpoint devices, securing corporate data, implementing access controls, integrate Azure AD for user authentication and policy enforcement and  more... 


**Summary Activities:**

- Device Enrollment and configuration:
    - Enroll corporate-owned or BYOD devices , set and manage policies, profiles, and configurations to ensure devices comply with organizational standards.
  
- Application Deployment and configuration:
    - Deploy and manage apps, apply app protection policies to protect corporate data.

- Create and Deploy Security Policy: 
    - Implement and deploy security baselines and policies to protect devices from threats and vulnerabilities for both endpoints, users and applications.

- Integrate Azure AD with Intune: 
    - Leverage Azure AD for user authentication and to enforce access policies across devices and apps.

- Remote Actions and Troubleshooting: 
    - Remotely wipe corporate data from lost or stolen devices to prevent unauthorized access, or lock them from access.

- Single Sign-On (SSO): 
    - Enable users to sign in once for seamless and secure user access to corporae resources.

- Patch Management: 
    - Manage and deploy Windows updates to devices, ensuring they are up-to-date with the latest security patches and feature updates.

- Conditional Access and Multi-Factor Authentication (MFA): 
    - Strengthen security by enforcing conditional access policies for accessing corporate resources.

----------------------------------------------------------------------


First step, provide a correct license to Intune Administrator from Microsoft 365 Admin Center.  
To achieve this, I'll heaad over to my Microsoft 365 admin portal here, https://admin.microsoft.com/  
I'll now assign **Enterprise Mobility + Security E5** license to my Admin account NNN@trialsc200lab.onmicrosoft.com so this user can perform all action that Intune has to offer.  
This is one of the eligible licenses.  
Because this account is already a Global Admin account, I do not need to seperately assign an "Intune Administrator" role to this account.  

![image](https://github.com/nahid7474/Intune/assets/170605912/9cf872c2-24a0-4272-be8b-3765d3bb6140)

I'll now use this account to log into Microsoft Intune Admin Center here https://intune.microsoft.com/ 

I have a brand new Intune admin center now.

![image](https://github.com/nahid7474/Intune/assets/170605912/d1071010-fb5f-47fb-b491-1b1e4d79b3a7)


Next, **Automatic Device Enrollment and configuration**

Before creating automatic enrollment policy, it is important to create groups.  
Groups in Microsoft Intune are essential organizational units that allow administrators to categorize and manage devices, users, and applications effectively.  
They can be classified into device, user, security, and dynamic groups, each serving specific management purposes.  
It is very effective for deployment and management of a specific targetted device, apps or users using groups.
This is also an ideal way to test a smaller unit of user or device based on their membership so everything else stays untouched. 

So, as a first step, I'll create a group

![image](https://github.com/nahid7474/Intune/assets/170605912/b4acd55e-41dc-436b-9980-84b82ac4f0ae)

Will keep the type as a Security group, name it as MDMTestGroup1-NahidHomeLab, Test GRoup 1 as description, Membership type: Assigned. 

![image](https://github.com/nahid7474/Intune/assets/170605912/67ef585e-613d-4114-9086-8c5903d3d195)


A note on different group types:  
**Security Groups**: Primarily used for controlling access to resources and applying security policies across various Microsoft services, focusing on access permissions and security enforcement.  

**Microsoft 365 Groups**: Designed for collaboration and communication within the Microsoft 365 ecosystem, integrating across applications like Outlook, Teams, SharePoint, and OneDrive to facilitate shared resources and collaborative workflows.  

Now with the membership types:  
**Assigned Membership Type**: Memberships are manually managed by administrators, making it suitable for assigning specific policies, profiles, or applications to predefined groups of devices or users based on static criteria.  
Dynamic Membership Type: Membership is automatically determined based on rules or filters defined by administrators, allowing for dynamic inclusion or exclusion of devices or users based on changing attributes like device properties, user roles, or Azure AD attributes.  
**Dynamic Device Membership Type**: Similar to dynamic groups, dynamic device membership automatically adjusts based on specified criteria, specifically focusing on devices and their properties, ensuring policies and configurations are dynamically applied as devices meet or no longer meet defined conditions.

Next, assign members to this group

Will select 2 users from the list (note: these users came already from my Infrastructure setup project), CLick Create

![image](https://github.com/nahid7474/Intune/assets/170605912/3bc2aa65-bb16-4dfe-b4bd-1de807228020)

Group has now been successfully created. 

![image](https://github.com/nahid7474/Intune/assets/170605912/17b5ca84-45b2-4410-b53d-9834ce205c93)

Next, assign license to this group: Enterprise Mobility + security E5  
Licenses > Assignments


![image](https://github.com/nahid7474/Intune/assets/170605912/6e1fe038-4cc6-4a97-b54b-6286ba3aacd4)

Check the box, click Save  

![image](https://github.com/nahid7474/Intune/assets/170605912/94c5c1cc-cdf1-434e-a989-e82e10c975b3)  


Now that I have my group created, licenses assigned to the group members, I am ready to configure MDM (Mobile Device Management) user scope and MAM (Mobile App Management) user scope.  
To do this, navigate to Devices > Enrollment > Automatic Enrollment from the home page.  

![image](https://github.com/nahid7474/Intune/assets/170605912/a2198ee1-31e1-4e8a-94ff-ab1f26706332)


Select 'some' as the MDM scope, click 'No groups selected' to bring up the select groups pane, choose MDMTestGroup1-NahidHomeLab group and then click Select  
Click Save.

![image](https://github.com/nahid7474/Intune/assets/170605912/fc1e6513-e11a-4ce7-b7f6-8ecbeeaa2ae4)

I have my auto enrollment process created.  
Now, I'll test this auto enrollment process from one one of the users in the group that I've created earlier.  
I'll use user **nnahin10@trialsc200lab.onmicrosoft.com** from a windows 10 VM.  

Will navigate to Settings > Access work or school > Connect  

![image](https://github.com/nahid7474/Intune/assets/170605912/d972cde3-0664-4c64-8321-acf9660b24d3)

  
Click **'Join this device to Microsoft Entra ID'**

Use nnahin10@trialsc200lab.onmicrosoft.com account as this one is one of the member of MDMTestGroup1-NahidHomeLab group with an eligible license. 

![image](https://github.com/nahid7474/Intune/assets/170605912/cea573bc-af35-4273-b637-fe545b06a0bb)


Click join as as the right tenant and user have been picked up

![image](https://github.com/nahid7474/Intune/assets/170605912/a9ac39f2-0eef-4aaa-985c-ae6971a7f2d8)


All set, click Done. This should finish the onboarding process.  
To verify, I will sign out and sign in using the nnahin10@trialsc200lab.onmicrosoft.com account this time instead of a local admin user.  

![image](https://github.com/nahid7474/Intune/assets/170605912/04965d85-7e15-4434-b4da-9dbabb571971)

This time, click Other user, use nnahin10@trialsc200lab.onmicrosoft.com and log in

![image](https://github.com/nahid7474/Intune/assets/170605912/4a0a3d0a-1735-42f5-8ab7-5c076bda33be)

Click Ok

![image](https://github.com/nahid7474/Intune/assets/170605912/a3c1297b-7d9b-4895-8ce6-abdf018603cb)


Enter Password and Sign in, Action Required window pops up for 2FA set up , click Next

![image](https://github.com/nahid7474/Intune/assets/170605912/b7afd16e-0fc1-4df5-98e0-a48aea484c1d)

Click Next  

![image](https://github.com/nahid7474/Intune/assets/170605912/2c440eaf-aca1-4dfe-a3af-eb8fcfd097c8)

Register with phone authenticator app and respond to the prompt with Yes

![image](https://github.com/nahid7474/Intune/assets/170605912/0d742416-cd19-4042-936a-ddcb03122f40)

CLick Done.

![image](https://github.com/nahid7474/Intune/assets/170605912/498e17b2-4e43-429d-8b54-d842812f61f5)

Wait a moment for company policy to kick in.

![image](https://github.com/nahid7474/Intune/assets/170605912/b9a084f5-dbbe-45cc-9a48-08521e196459)

Click OK.

![image](https://github.com/nahid7474/Intune/assets/170605912/33f2995b-087a-46a3-aaed-d65ca86ca6a7)

Set up a PIN

![image](https://github.com/nahid7474/Intune/assets/170605912/195ecae1-3cc2-4a3b-aa25-9ac28d840c6b)

Click Next

![image](https://github.com/nahid7474/Intune/assets/170605912/68592490-39aa-433e-83f5-67f67b2d4b25)



And it's done with the setup and enrollment process.  
This computer is now connected to the NahidHomeLab domain via Microsoft Entra ID.  
To verify, go to Settings, Account > Access work or school. and it shows that the device is now part of the NahidHomeLab's Azure AD.  

![image](https://github.com/nahid7474/Intune/assets/170605912/0eef141d-e9c5-4c69-b88d-8cb8e53c97dd)

Click Info for more validation.  



To further validate, I'll go back to the Intune Admin Center and this newly enrolled device should be there.


![image](https://github.com/nahid7474/Intune/assets/170605912/e5cf2e23-8d03-466b-9330-f89d08fcc491)


As expected, the device is there, managed by Intune, ownership Corporate, compliant and primary user is nnahin10@trialsc200lab.onmicrosoft.com  



Next, **Application Deployment and configuration:**  

From the Intune admin center homepage, click Apps > Windows apps > Add > windows 10 and later in App type, click Select


![image](https://github.com/user-attachments/assets/33f091dc-cb62-4b91-b60c-3a743f6a0dc6)


Give this app suite a name and click Next to continue

![image](https://github.com/user-attachments/assets/5a7cc4ae-3ee2-4a61-8880-dd5a4ccc7ce2)


Will select the apps needed, choose default file format as Office OpenXML Format, update channek as Monthly Enterprise Channel as recommended by Microsoft
Click Next at the bottom to go to the Assignments page

![image](https://github.com/user-attachments/assets/b5f4688d-1ca5-448f-b432-0d1c2bae8385)


Will select my MDMTestGroup1-NahidHomeLab group as the target group under Available for enrolled devices, click Next

![image](https://github.com/user-attachments/assets/939eaf66-2c58-4472-bb83-17a19a6c34c9)


Review+Create

![image](https://github.com/user-attachments/assets/b74a1f37-4ca4-4fac-b733-86bab9bdc6b9)


Deployment successful.

Similarly, I'll deploy company portal app for all my users and devices

![image](https://github.com/user-attachments/assets/f529f361-39c9-4741-88b1-fd3e2a21c479)


In about 5 minutes this app got deployed on my client machine

![image](https://github.com/user-attachments/assets/ab1e3e9a-aae6-4c43-9ec4-0b0d55606406)


And, I can see now my deployed Office application there as expected

![image](https://github.com/user-attachments/assets/c3ac75ef-f641-4af7-8fdd-2d47964a6bd5)


They are just a click away from installation on eligible/compliant devices.

![image](https://github.com/user-attachments/assets/a9a79014-1c18-410c-a393-7d5af3cca48a)



Next stop, **Device compliance policy creation and deploy**

To do this, first I'll disable the default compliance policy that makes all enrolled device compliant by default. 

Click on any device that are enrolled

![image](https://github.com/user-attachments/assets/2f1206ca-fd89-48fc-bb65-0193080eb2d0)

This device was showing compliant but device compliant shows that it is on error state

![image](https://github.com/user-attachments/assets/73ebae6a-6ee5-4983-a238-25f406314a05)


Click Default Device Compliance Policy, there is no custom device policy assigned

![image](https://github.com/user-attachments/assets/b9ef8ecd-8f24-470b-8adc-bd1fd41fc0c6)


Will now change this by navigating to Devices > Compliance > Compliance settings  
Mark devices with no compliance as Non Compliant, change the validity period as 3 days, click Save    

![image](https://github.com/user-attachments/assets/b16d2155-25f6-484b-8ffb-b37af5920865)






Next stop, **Device compliance policy creation and setup**  

To create a new policy, click COmpliance from the Devices tab, click Create policy  
Closse platform as Windows 10 or later  
Click Create.  

![image](https://github.com/user-attachments/assets/a0747584-2a86-410d-8df9-575cc7273b2f)

Give it a name, click Next  

![image](https://github.com/user-attachments/assets/e47566fe-4866-43c5-bdb5-cfb68116a7d5)  


In COmpliance settings, will configure the policy as I need in line with my organization and security best proactices.  
In this case, I'll require bitlocker, require password to unlock mobile devices, set a Minimum password length, expiry date etc.  


![image](https://github.com/user-attachments/assets/553d431f-b2a2-469d-a734-89f367eb4461)


For Device Security, will turn Firewall as a requirement, as well as Antivitus, Antispyware, and Microsoft Defender Antimalware turned on.  
Click Next  


![image](https://github.com/user-attachments/assets/c8a2c1eb-6c7b-4aab-bb36-63c7f4b9edaf)


If the device doesn't meet all the required policies/standards set above, I'll mark the device as non-compliant immediately and add this device to retire list.  
Click Next.  

![image](https://github.com/user-attachments/assets/87ee2e0c-c95e-4f98-892f-9f98584260c5)

To apply these policies to all users and devices, I'll add all devices and users group.  
If I want I can exclude a group of users or devices to exempt from this polices (exceptional cases)  
In that case, I'll add that group to the Excluded group list.  
CLick Next  

![image](https://github.com/user-attachments/assets/0a6f176d-d424-40fb-ba75-77ec6282f621)

Review + Create


![image](https://github.com/user-attachments/assets/b019e3e3-a943-451a-85f6-6eb2461e2b44)

Now the devoce policy profile is successfully created as per the organisational standat and best practices.  



