# ActiveDirectory

## Project description:

The main objective of Active Directory is to provide centralized identification and authentication services to a network of computers using the Windows system. It also enables the assignment and enforcement of policies, the distribution of software, and the installation of critical updates by administrators.
Active Directory lists items in a managed network such as user accounts, servers, workstations, shared folders, printers, and more. It aims at making it easy for a user to find shared resources, and allows administrators to control their usage through distribution, duplication, partitioning, and secure access to listed resources.

## Part I: Active Directory configuration

1. We installed Windows Server 2016 Standard in a VM.

![image](https://user-images.githubusercontent.com/56129562/149035634-199a6e52-5888-4421-b71c-818feefd13e2.png)

2. Now let's install Active Directory, we just need to follow these steps:

![Configure this local server](https://user-images.githubusercontent.com/56129562/149035682-63a03d39-25a8-401d-babf-360650b6086e.png)

![WELCOME TO SERVER MANAGER](https://user-images.githubusercontent.com/56129562/149035694-a0057d0f-f755-4815-b188-e9962eaba813.png)

![WELCOME TO SERVER MANAGER](https://user-images.githubusercontent.com/56129562/149035718-6039e775-d952-44bc-a8bd-4dbfa6ec9d66.png)

![WELCOME TO SERVER MANAGER](https://user-images.githubusercontent.com/56129562/149035736-d19b0443-a014-4b84-ba8f-49c65bfad35d.png)

![WELCOME TO SERVER MANAGER](https://user-images.githubusercontent.com/56129562/149035767-9feb640d-a7bd-41c4-82b0-478a7ff51f66.png)


![Confirm installation selections](https://user-images.githubusercontent.com/56129562/149035780-f120d7b0-e451-47df-a094-8fd330c878a0.png)

After the installation of AD, we need to configure it for the first time.

First, we need to add a new forest , in which we are going to mention our domain `medmac.me`.

![WhatsApp Image 2022-01-17 at 16 38 53](https://user-images.githubusercontent.com/53974876/149802227-98a50e95-94d7-4f5e-861f-308688bce629.jpeg)

We need to assign a password to our default user.

![Domain Controller Options](https://user-images.githubusercontent.com/56129562/149035885-57cafbc3-46c9-43ca-91cb-a77f2d9fa180.png)




**Note**: We can create a `.bat` script to do all this stuff for us.

![WhatsApp Image 2022-01-17 at 16 38 55](https://user-images.githubusercontent.com/53974876/149803405-095ccac3-1d05-4b21-ad66-272bae1c9c7e.jpeg)


![WhatsApp Image 2022-01-17 at 16 38 54](https://user-images.githubusercontent.com/53974876/149803729-c9ec3d61-f7e8-48a0-9117-cdb2b0fdbb85.jpeg)


After the installation we restart the server.


## Adding a user to the domain
We create a new user `ouhidaoui@medmac.me`. And add it to the domain.

![WhatsApp Image 2022-01-17 at 16 38 54 (1)](https://user-images.githubusercontent.com/53974876/149804098-529d7aab-b598-4953-a7d5-b13f19bf59f3.jpeg)

![WhatsApp Image 2022-01-17 at 16 38 54 (2)](https://user-images.githubusercontent.com/53974876/149804362-eb58c480-7448-46ea-8af2-36d8d72edb29.jpeg)

**Note**: In order to avoid any login problems, we need to explicitely allow the user to log in into his account. To do so, we need to add it to the `Allow log on locally` policy.

![Allow log on locally Properties](https://user-images.githubusercontent.com/56129562/149036697-0ffcb40d-2266-4025-a87d-f4218e9c1a53.png)

For the first time, we must change the password to log in.
![WhatsApp Image 2022-01-17 at 16 38 11](https://user-images.githubusercontent.com/53974876/149804679-71b0fad5-4bda-4af3-b1bf-795c54bae62b.jpeg)




![Pasted Graphic 18](https://user-images.githubusercontent.com/56129562/149036941-a852cc63-0c76-487b-85ce-b0709634224e.png)



