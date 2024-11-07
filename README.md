# WINDOWS SERVER - ACTIVE DIRECTORY

## Objective
The goal of this lab is to design and configure a comprehensive Windows Server environment using Active Directory, Group Policy Objects (GPOs), and Network File Sharing. The lab aims to demonstrate the setup and management of essential Active Directory features, including creating Organizational Units (OUs), user accounts, and groups, while implementing security measures through GPOs. Additionally, it focuses on configuring network file sharing and permissions, setting up mapped drives, and establishing service accounts to streamline system administration tasks. This hands-on experience enhances the understanding of server management, network configurations, and security practices within a Windows Server infrastructure.



## Hardware Requierements
- VMware Workstation Pro - 1.2 GB Disk Space and 64-bit OS

- Windows Server 2022- 2GB Memory, 20GB Disk Space

- Windows 10 Pro - 2GB Memory, 20GB Disk Space (minimum)





## Lab Setup
-	**Set Up a Virtual Lab Environment:**
   
- Use virtualization software like VMware Workstation, Hyper-V, or VirtualBox.

- Install Windows Server (preferably Windows Server 2019 or later) and configure it as a domain controller.

- Install a couple of Windows client machines (e.g., Windows 10 or Windows 11 Enterprise of Pro) and join them to the domain.



## Hands-On Activities
1.	**Install Active Directory Tools and Promote as DC**
-	Open Server Manager

o	Log in to your Windows Server (Windows Server 2019 or 2022 recommended).

o	Open Server Manager. It should open automatically after logging in, or you can search for "Server Manager" in the Start menu.
-	Add Roles and Features

o	In Server Manager, click on Manage in the top-right and select Add Roles and Features.

o	Select Role-based or feature-based installation and click Next.

-	Select the Server

o	Choose the server from the Select a server from the server pool list and Click Next.

-	Install Active Directory Domain Services (AD DS)

o	On the Select server roles page, check Active Directory Domain Services.

o	Click Add Features when prompted, and then click Next.

o	Click Next on the AD DS page (no additional features are needed).

o	On the Confirmation page, click Install.

-	Promote the Server to a Domain Controller

o	Once the installation completes, you’ll see a notification in Server Manager. Click Promote this server to a domain controller.

o	Choose Add a new forest and enter your Root domain name (e.g., example.local), then click Next.

-	On the Domain Controller Options page:

o	Choose the Forest functional level and Domain functional level (usually "Windows Server 2016" or higher).

o	Make sure Domain Name System (DNS) server and Global Catalog (GC) are checked.

o	Enter a Directory Services Restore Mode (DSRM) password.

o	Click Next through the rest of the screens (DNS options, Additional options, etc.).

o	On the Paths page, leave the default paths and click Next.

o	On the Review Options page, click Next to proceed.

o	In the Prerequisites Check, click Install.

-	Verify the Domain Controller

o	After the server restarts, log in using your domain credentials.

o	Open Server Manager > Tools > Active Directory Users and Computers to verify that Active Directory is installed and running.

2.	**Creating Organizational Units (OUs)** 
   
	●	Objective: Organize the directory structure.

o	Open Active Directory Users and Computers (ADUC).

o	Create OUs for Different Geographical Locations (e.g., USA, Europe, Asia)
	-	Right-click the domain name and select New > Organizational Unit.
 
o	Create a nested OU inside the locations (e.g., USA > Computers, Users, Service Accounts)

o	Create a nested OU inside Computers (e.g., IT > Servers)

o	Create a nested OU inside Users (e.g., Accounting, HR, IT).

![image](https://github.com/user-attachments/assets/122787bf-03c7-4c3e-a6f5-dd8cdae971f2)

3.	**Creating User Accounts**
   
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

4. 	**Creating Groups**
- 	Objective: Create security and distribution groups.

o	Navigate to an OU (e.g., HR).

o	Right-click the OU and select New > Group. 

o	Name the group (e.g., #HR_Department).

o	Select the group scope (e.g., Global) and type (e.g., Security).

![image](https://github.com/user-attachments/assets/96b6da2d-c3a4-4f79-96ec-1c53e8373973)

5.	**Adding Users to Groups**
   
-	Objective: Manage group memberships.

o	Open the properties of a user account (e.g., jdoe).

o	Go to the Member Of tab.

o	Click Add and select the group (e.g., #HR_Department).

o	Verify the membership.

o	Do the same for another user in the HR OU

o	Add user in the OU IT to Domain Admins Group

6.	**Configure Network settings for the Server**

o	Change the domain controller’s IP address to static IP

o	Change DNS Servers to loopback and google DNS

7.	**Join Windows Client to the Domain**

o	Change the DNS server of the computer to the DC IP and google DNS

o	Join the computer to the domain and move the computer to the appropriate OU

o	Login with the user created in Active Directory (e.g., John Doe)

8.	**Creating and Linking Group Policy Objects (GPOs)**
	
-	Objective: Create and link policies to OUs.

o	Open Group Policy Management Console (GPMC).

o	Right-click the domain or an OU and select Create a GPO in this domain, and Link it here.

o	Name the GPO (e.g., Password Policy).

o	Edit the GPO and configure settings (e.g., minimum password length, password complexity).

o	Link the GPO to the desired OU.

o	Create more GPO to Restrict Control Panel Access, Block USB Drives and Set a default desktop wallpaper for all users

9.	**Configuring File Sharing and Permissions**

-	Objective: Set up file sharing within the AD environment

o	Create a network share (e.g., \\ServerName\SHARED). Create a folder named "SHARED" on the C: drive.

o	Set Folder Properties

-	Right-click the folder and select "Properties."

-	Go to the "Sharing" tab

o	Share the Folder

-	Click "Advanced Sharing."

-	Check "Share this folder" and provide a share name (e.g., "SharedFiles").

-	Click "Permissions" and set the share permissions (e.g., "Everyone" with "Read" access).

o	Set NTFS Permissions

-	Go to the Security Tab. In the folder properties, go to the "Security" tab.

-	Edit Permissions

-	Click "Edit" to modify the NTFS permissions.

-	Add the appropriate users or groups and assign the necessary permissions (e.g., "Read & Execute," "Modify," etc.).

10.	**Map Network Drives via Group Policy**

o	Open Group Policy Management

-	On the domain controller, open the Group Policy Management Console (GPMC).

o	Create a GPO

-	Create a new GPO (e.g., Mapped Drive).

o	Configure Drive Mapping

-	Navigate to User Configuration -> Preferences -> Windows Settings -> Drive Maps.

-	Right-click and select "New" -> "Mapped Drive."

-	Set the location (e.g., \\ServerName\SHARED) and choose a drive letter.

-	Configure additional settings as needed (e.g., "Reconnect," "Label as," etc.).

o	Link the GPO

-	Link the GPO to the appropriate Organizational Unit (OU) that contains the users who need access to the shared folder.

o	Update Group Policy

-	On the client computers, update the group policy by running gpupdate /force in the command prompt or simply restart the computers.

11.	**Creating Service Accounts**
	
-	Objective: Create and configure a service account.

o	Navigate to the appropriate OU (e.g., Service Accounts).

o	Right-click the OU and select New > User.

o	Fill in the service account details (e.g., $Autologin) for name and set a Description.

o	Set a strong password and configure the account settings (e.g., password never expires, cannot change password).

o	Assign the necessary permissions to the service account on the relevant resources.

o	Set up with a client machine using Windows Autologon tool (sysinternals)

12.	**Configuring Account Lockout Policy**

-	Objective: Set up account lockout policies to enhance security.

o	Open GPMC and create a new GPO (e.g., Account Lockout Policy).

o	Edit the GPO:

-	Navigate to Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy.

-	Configure the settings (e.g., Account lockout threshold, Account lockout duration, Reset account lockout counter after).

o	Link the GPO to the desired OU.


## Testing and Verification

1.	Verify User Logon: Log on to a client machine using one of the newly created user accounts.
2.	Check Group Membership:
-	Open a Command Prompt and run gpresult /r to verify applied policies and group memberships.
3.	Test GPOs:
-	Log on to a client machine with a user account that has GPOs configured and verify that the GPOs were applied.
4.	Test Network Drives:
-	Log on to a client machine with a user account that has Drive Mapping GPO configured and verify that they can access the network folder.




