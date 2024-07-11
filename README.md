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
I'll heaad over to my Microsoft 365 admin portal here, https://admin.microsoft.com/  
I'll now assign **Enterprise Mobility + Security E5** license to my Admin account NNN@trialsc200lab.onmicrosoft.com so this user can perform all action that Intune has to offer.  
This is one of the eligible licenses.  
Because this account is already a Global Admin account, I do not need to seperately assign an "Intune Administrator" role to this account.  

![image](https://github.com/nahid7474/Intune/assets/170605912/9cf872c2-24a0-4272-be8b-3765d3bb6140)

I'll now use this account to log into Microsoft Intune Admin Center here https://intune.microsoft.com/ 

I have a brand new Intune admin center now.

![image](https://github.com/nahid7474/Intune/assets/170605912/d1071010-fb5f-47fb-b491-1b1e4d79b3a7)


Next, **Automatic Device Enrollment and configuration**

