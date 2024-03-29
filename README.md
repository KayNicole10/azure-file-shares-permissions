# azure-file-shares-permissions
<p align="center">
<img src="https://i.imgur.com/vtSRnet.png" alt="Creating Network File Shares and Permissions"/>
</p>

<h1> Creating Network File Shares and Permissions</h1>
In this tutorial, I will be creating different file shares that allow "Read" or "Write" access, and deny access to certain users or groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10 
- Windows Server 

<h2>Steps</h2>

- Step 1: Create Sample File Shares with Various Permissions
- Step 2: Attempt to Access File Shares as a Normal User
- Step 3: Create an “ACCOUNTANTS” Security Group and Assign Permissions


<h2>Actions and Observations</h2>

<h3>Step 1: Create Sample File Shares with Various Permissions</h3>

<p>
<img src="https://i.imgur.com/M1s7psx.png" height="80%" width="80%" alt="4 folders"/>
</p>
<p>
Begin by logging into the Windows Server (DC-1) using the domain admin account (mydomain.com\jane_admin). Then, log into Windows 10 (Client-1) as a regular user (mydomain\labuser). On DC-1, navigate to the C:\ drive and create four folders: "read-access," "write-access," "no-access," and "accounting."
</p>
<p>
<img src="https://i.imgur.com/n95UTeM.png" height="80%" width="80%" alt="permissions"/>
</p>
<p>
Set the following permissions for the “Domain Users” group:
</p>

<h4>Folder: “read-access”, Group: “Domain Users”, Permission: “Read”</h4>

<img src="https://i.imgur.com/QrAgoJh.png" height="80%" width="80%" alt="Read"/>
<img src="https://i.imgur.com/3Ajp333.png" height="80%" width="80%" alt="read-access"/>

<h4>Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”</h4>

<img src="https://i.imgur.com/LMw7vBg.png" height="80%" width="80%" alt="Read/Write"/>
<img src="https://i.imgur.com/WM9RbeT.png" height="80%" width="80%" alt="write-access"/>

<h4>Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”</h4>

<img src="https://i.imgur.com/c6IRNVB.png" height="80%" width="80%" alt="Domain Admins"/>
<img src="https://i.imgur.com/C0iUu2I.png" height="80%" width="80%" alt="no-access"/>

</p>

<br />

<h3>Step 2: Attempt to Access File Shares as a Regular User</h3>

<p>
<img src="https://i.imgur.com/k7cJWdk.png" height="80%" width="80%" alt="Regular User"/>
</p>
<p>
As a regular user on Client-1, attempt to access file shares by navigating to the shared folder. Use the "start" command followed by "run" and then enter "\dc-1" to access the shared folders hosted on the DC-1 server. Try to access the folders within this shared directory to test and verify the user's permissions. 
</p>
<p>
<img src="https://i.imgur.com/YCc7Xdp.png" height="80%" width="80%" alt="shared folder"/>
<img src="https://i.imgur.com/aYjhuQ1.png" height="80%" width="80%" alt="\dc-1"/>
</p>
<p>
<img src="https://i.imgur.com/FfZ1Whc.png" height="80%" width="80%" alt="no access"/>
No Access: As a regular non-admin user, we do not have permission to access this file. 
</p>
<p>
<img src="https://i.imgur.com/GN4GkNR.png" height="80%" width="80%" alt="write access"/>
Read/Write Access: We have permission to create text documents in this file.
</p>
<p>
<img src="https://i.imgur.com/yItAmS5.png" height="80%" width="80%" alt="read access"/>
We do not have permission to create text documents In this file. We can only view them. 
</p>
<br />

<h3>Step 3: Create an “ACCOUNTANTS” Security Group and Assign Permissions</h3>

<p>
Return to the DC-1 server and navigate to Active Directory. Create a security group named "ACCOUNTANTS." Then, modify the permissions for the "accounting" folder previously created, assigning the "ACCOUNTANTS" group with "Read/Write" permissions. 
</p>
<p>
<img src="https://i.imgur.com/H927xJZ.png" height="80%" width="80%" alt="ACCOUNTANTS."/>
<img src="https://i.imgur.com/o4qSOQk.png" height="80%" width="80%" alt="Read/Write"/>
<img src="https://i.imgur.com/W8ODtFS.png" height="80%" width="80%" alt="accounting"/>
</p>
<p>
As a regular user on Client-1, attempting to access the "accountants" folder should fail because the user lacks the necessary permissions.
</p>
<p>
<img src="https://i.imgur.com/oMfDY9m.png" height="80%" width="80%" alt="lacks"/>
</p>
<p>
After logging out of Client-1, navigate to the DC-1 server and add the user to the "ACCOUNTANTS" Security Group. 
</p>
<p>
<img src="https://i.imgur.com/0SMIL3M.png" height="80%" width="80%" alt="Security"/>
</p>
<p>
Upon signing back into Client-1 as the regular user and attempting to access the "accounting" share in \DC-1, the access should now be successful since the user has been granted the appropriate permissions through membership in the "ACCOUNTANTS" group.
</p>
<p>
<img src="https://i.imgur.com/8jsTUzL.png" height="80%" width="80%" alt="regular user"/>
<img src="https://i.imgur.com/u5e1y4h.png" height="80%" width="80%" alt="access"/>
</p>
<br />
