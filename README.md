# WINDOWS SERVER - ACTIVE DIRECTORY

## Objective
The goal of this lab is to design and configure a comprehensive Windows Server environment using Active Directory, Group Policy Objects (GPOs), and Network File Sharing. The lab aims to demonstrate the setup and management of essential Active Directory features, including creating Organizational Units (OUs), user accounts, and groups, while implementing security measures through GPOs. Additionally, it focuses on configuring network file sharing and permissions, setting up mapped drives, and establishing service accounts to streamline system administration tasks. This hands-on experience enhances the understanding of server management, network configurations, and security practices within a Windows Server infrastructure.



## Hardware Requierements
- VMware Workstation Pro - 1.2 GB Disk Space and 64-bit OS

- Windows Server 2022- 2GB Memory, 20GB Disk Space

- Windows 10 Pro - 2GB Memory, 20GB Disk Space (minimum)





## Lab Setup
1.	Set Up a Virtual Lab Environment:
   
- Use virtualization software like VMware Workstation, Hyper-V, or VirtualBox.

- Install Windows Server (preferably Windows Server 2019 or later) and configure it as a domain controller.

- Install a couple of Windows client machines (e.g., Windows 10 or Windows 11 Enterprise of Pro) and join them to the domain.



## Hands-On Activities
1.	Install Active Directory Tools and Promote as DC
2.	Creating Organizational Units (OUs)
   
	●	Objective: Organize the directory structure.

o	Open Active Directory Users and Computers (ADUC).

o	Create OUs for Different Geographical Locations (e.g., USA, Europe, Asia)
	-	Right-click the domain name and select New > Organizational Unit.
 
o	Create a nested OU inside the locations (e.g., USA > Computers, Users, Service Accounts)

o	Create a nested OU inside Computers (e.g., IT > Servers)

o	Create a nested OU inside Users (e.g., Accounting, HR, IT).

![image](https://github.com/user-attachments/assets/122787bf-03c7-4c3e-a6f5-dd8cdae971f2)

3.	Creating User Accounts
   
	●	Objective: Create user accounts with specific attributes.

o	Navigate to the appropriate OU (e.g., HR).

o	Right-click the OU and select New > User.

o	Fill in the user details:
-	First Name: John
-	Last Name: Doe
-	User Logon Name: jdoe
  
o	Set a password and configure the account settings (e.g., password never expires).

o	Set a Description for John Doe (e.g., Recruiter)

o	Create more users for IT and Accounting OU following the steps above

![image](https://github.com/user-attachments/assets/332670ba-85a8-4bc6-8393-55e72eceb36e)

4. 	Creating Groups
- 	Objective: Create security and distribution groups.

o	Navigate to an OU (e.g., HR).

o	Right-click the OU and select New > Group. 

o	Name the group (e.g., #HR_Department).

o	Select the group scope (e.g., Global) and type (e.g., Security).



