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


Now that I have my group created, I am ready to configure MDM (Mobile Device Management) user scope and MAM (Mobile App Management) user scope.  
To do this, navigate to Devices > Enrollment > Automatic Enrollment from the home page.  

![image](https://github.com/nahid7474/Intune/assets/170605912/a2198ee1-31e1-4e8a-94ff-ab1f26706332)





