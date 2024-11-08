# Windows 10 Client Domain Join

## Description
This project demonstrates the process of connecting a Windows 10 client to an existing Active Directory (AD) domain hosted on Windows Server 2016. The aim was to showcase the step-by-step procedure and verification steps needed for successful domain integration. This includes configuring network settings, joining the domain, and confirming authentication and access in AD.

## Tools and Utilities

- **Windows Server 2016**: Hosted the Active Directory Domain Services (AD DS) and DNS.
- **Windows 10**: Client system used for domain joining and testing.
- **Active Directory Users and Computers (ADUC)**: Managed user and computer accounts.
- **Server Manager**: Used for navigating AD tools and monitoring the server.
- **Command Prompt**: Verified domain user information using commands like `whoami`.

## Environments

### Server Environment
- **Operating System**: Windows Server 2016 configured with AD DS and DNS.
- **Network Configuration**: The server was set up with an internal network to enable seamless communication between the server and client.

### Client Environment
- **Operating System**: Windows 10 configured to join the domain.
- **Network Settings**: Configured to use an internal network for connectivity with the AD server.

## Program Walkthrough

### Initial Network Configuration
1. On the Windows 10 client, accessed **Network and Sharing Center** → **Change Adapter Settings**.
2. Configured **Internet Protocol Version 4 (TCP/IPv4)** settings to set the DNS to point to the Domain Controller's IP.

### Joining the Domain
1. Navigated to **System** → **Advanced system settings** on the Windows 10 client.
2. Clicked **Change** under **Computer Name** settings and selected the **Domain** radio button.
3. Entered the domain name (e.g., `DOMAIN.local`) and provided administrator credentials for authentication.
4. Confirmed successful domain join with a welcome message and rebooted the client.

### User Authentication
1. After reboot, logged in using domain credentials via the **Other User** option on the login screen.
2. Verified the domain user login by running the `whoami` command, which displayed the domain and user information.

### Validation in Active Directory
1. On the server, accessed **Server Manager** → **Tools** → **Active Directory Users and Computers**.
2. Confirmed that the client computer was listed in the **Computers** container within AD, indicating successful registration.

## Scenario
A new joiner has just been hired. Create a user account for the new hire

</br>
1. In Server Manager under Tools, navigate to **Active Directory Users and Computers.** Under the Users container, a list of all users within AD
![8e70de9c-0e39-42a7-80e5-8a496595e4e0](https://github.com/user-attachments/assets/092b7bb3-1fb8-4056-ad42-6f659fede89f)


![image 1](https://github.com/user-attachments/assets/8c94adf4-b5cf-45a4-b972-82e22ec851ff)

![image 2](https://github.com/user-attachments/assets/fe290acf-f0d5-4c12-803a-83bcd12c2dac)

2. Right-click the **Users** container and select **New → User.** Input new hires name and user logon name, then select **Next.** Create a password for the New Hire and select **Next** then **Finish**
    1. Normal the checkbox for **User must change password at next logon** will be selected in order to help with security 
    2. The password set for the user will be provided the first time, and when the logon, they will be required to change the password 

![image 3](https://github.com/user-attachments/assets/855e7d32-ef38-46fe-ba62-70fa1ac0ab1f)

![image 4](https://github.com/user-attachments/assets/5559bbc8-04bb-412a-8368-3e0fbc298b65)

![image 5](https://github.com/user-attachments/assets/d8b0630d-dc98-4116-80a7-f9b8c8093961)

3. The new user will now be added to the Users Container

![image 6](https://github.com/user-attachments/assets/8fe29a6d-9178-445d-a69c-0fa0ba621364)

## Domain Join

Both Client PC and Server MUST BE ON THE SAME NETWORK. Otherwise it wont work. For VMs set both VMs Network Settings to **Internal**

1. On a guest client machine, navigate to **Network and Sharing Center → Change Adapter Settings →** right-click **Ethernet** and select **Properties**

![image 7](https://github.com/user-attachments/assets/f7cbd8c1-b823-4376-bc3a-c754f2dd9f93)

![image 8](https://github.com/user-attachments/assets/36eb8cec-b746-4eac-b371-1e5f4e679b7b)

2. Under Properties, select **Internet Protocol Version 4 (TCP/IPv4)** and choose properties. Input valid IP configurations and under DNS server, input the value of the **Domain Controller** 

![8e70de9c-0e39-42a7-80e5-8a496595e4e0](https://github.com/user-attachments/assets/e850369a-b6b7-4eb0-b03f-e719cb658ce5)

![image 9](https://github.com/user-attachments/assets/88dc1ca7-2096-4d00-85a1-6e0927012db4)

3. Navigate back to **System** on the Windows Client and select **advanced system settings.** Select the **Change** to change the domain of the Client

![image 10](https://github.com/user-attachments/assets/25477936-5255-4c7d-aabc-a69de62208c8)

![image 11](https://github.com/user-attachments/assets/06effae5-94f7-4dac-a89c-5bfe2b4b297a)

4. Check the **Domain** radio button and specify the domain of the **Domain Controller** that was created previously. 

![image 12](https://github.com/user-attachments/assets/10350e4a-0035-472d-ae27-9ac549766618)

![image 13](https://github.com/user-attachments/assets/60d692a6-1d8e-46a2-b414-6fc69b3d7bb4)

5. Once the domain is input, provide user credentials for the domain account. Will then receive a Welcome message if joined to the domain. Reboot once finished.

![image 14](https://github.com/user-attachments/assets/5e9d20ce-4816-496f-a7f5-817cbd80844d)

![image 15](https://github.com/user-attachments/assets/f3799b27-b35a-4f3c-98cf-a06202520b06)

6. Now that the machine is rebooted, login credentials for any user within that domain can be used on the Windows Client to login by selecting **Other User** when prompted to login. 
    1. ie. - The Marty Jones account created earlier will be used to login
    2. Now logged in and authenticated as Marty Jones
    3. Can run the **whoami** command in cmd and it will provide the domain\username of the individual logged in at the moment

![image 16](https://github.com/user-attachments/assets/88338a9c-71ec-4e6d-9370-974cbc359300)

![image 17](https://github.com/user-attachments/assets/2b640d17-70fc-433b-9006-61910c7f4f90)

7. Under the Domain Controller, navigate to **Server Manager → Tools → Active Directory Users and Computers**

![image 18](https://github.com/user-attachments/assets/18f3f63a-00ef-4949-bddb-b5d0fb03af0e)

8. Under the **Computers** container, it can be seen that the **Computer** **Name** of the Windows Client previously registered to the domain is now in the container. Joining that computer to the domain created a computer account in AD

![image 19](https://github.com/user-attachments/assets/c0f754bc-45cc-42c7-b774-6666147a6713)

