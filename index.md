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

![WhatsApp Image 2022-01-17 at 20 58 18](https://user-images.githubusercontent.com/53974876/149830640-a2ae32f8-add4-4ef1-89da-a0472b757f1b.jpeg)

For the first time, we must change the password to log in.
![WhatsApp Image 2022-01-17 at 16 38 11](https://user-images.githubusercontent.com/53974876/149804679-71b0fad5-4bda-4af3-b1bf-795c54bae62b.jpeg)

Roaming Profiles
A profile is a folder that contains all the settings pertaining to a user’s working environment. By default, the profile is stored in the C:\Users directory. A roaming profile, on the other hand, is stored on a network instead on the local drive of the machine where you are logged. A Roaming profile is cached locally by default. The advantage of a roaming profile is that a user can log into any machine in the domain and have a consistent working environment.

First, we need to create a Roaming folder and share it across the network.



![Pasted Graphic 18](https://user-images.githubusercontent.com/56129562/149036941-a852cc63-0c76-487b-85ce-b0709634224e.png)


![WhatsApp Image 2022-01-17 at 19 20 06](https://user-images.githubusercontent.com/53974876/149830456-848fa18d-b181-4ef8-a92c-fe9627d724dd.jpeg)


![WhatsApp Image 2022-01-17 at 21 01 35](https://user-images.githubusercontent.com/53974876/149830892-1c28de94-8b9c-4b20-9b10-2283029bde48.jpeg)


Final Results:


![WhatsApp Image 2022-01-17 at 21 08 08](https://user-images.githubusercontent.com/53974876/149831687-62577463-edeb-421d-babf-1b65d89c86ea.jpeg)

We can map the folders as a network drive

![WhatsApp Image 2022-01-17 at 20 57 15](https://user-images.githubusercontent.com/53974876/149831851-33d3c304-b9c0-449d-ae2f-90c9cbdc2fba.jpeg)

Mandatory profiles
A mandatory user profile is a roaming user profile that has been pre-configured by an administrator to specify settings for users. ... Configuration changes made during a user's session that are normally saved to a roaming user profile are not saved when a mandatory user profile is assigned.

![WhatsApp Image 2022-01-17 at 21 14 30](https://user-images.githubusercontent.com/53974876/149832264-8d8c03d6-5fe0-49dc-937a-fbf28b306fe9.jpeg)

We create a new mandatory user, which is a basic user.

After the first login, we get the following message;

![149037294-369ebd29-5a19-43da-8a85-2286d8376164](https://user-images.githubusercontent.com/53974876/149832439-3ef50818-23f7-4cfc-8e88-aab7e70d5f4d.png)


![You've been signed in with temporary](https://user-images.githubusercontent.com/56129562/149037303-12a4a745-fbd2-4964-b770-dcc1ad56a0b1.png)



# Part II: Active Directory Groups

Groups in Active Directory allow to assemble any type of object (user account, computer account, group) into a single entity in order to simplify administrative work in an Active Directory forest. In addition, the groups are characterized by their scope, which will limit their application in the forest. But also by their type, they can be assigned security authorizations if their type allows it.
1. We Create three organizational units that will allow you to manage and organize users and user groups. We name them respectively `Casablanca` , `Fez` and `Rabat`.

![WhatsApp Image 2022-01-17 at 20 56 59](https://user-images.githubusercontent.com/53974876/149832827-36e4d201-d952-45ef-a734-a2edfc1f0d01.jpeg)


![WhatsApp Image 2022-01-17 at 19 20 30](https://user-images.githubusercontent.com/53974876/149832770-ab287cdf-1c2f-4dbb-ac83-cde7d229108b.jpeg)

We create 3 new users for each organizational unit. The result will look like this.

![WhatsApp Image 2022-01-17 at 20 56 57](https://user-images.githubusercontent.com/53974876/149832860-b018c0ea-86e4-4a89-89dd-d5776742020f.jpeg)


# Part III: Group Policy Object

Group Policies (or GPO for Group Policy Object) are centralized management functions of the Microsoft Windows family. They allow the management of computers and users in an Active Directory environment. Group Policies are part of the IntelliMirror family of technologies, which include managing disconnected computers, managing roaming users or managing folder redirection, and managing files in offline mode.

1. Apply a security policy for the user `Sales-dir-casablanca`, which will prevent the user from having the “control panel configuration” in the start menu.



![WhatsApp Image 2022-01-17 at 21 17 09](https://user-images.githubusercontent.com/53974876/149835136-1d982c4e-a8eb-43da-ab48-9dfc80e15ccc.jpeg)

First we need to create a new GPO (Group Policy Object)

Then we need to add the user to this GPO:

![WhatsApp Image 2022-01-17 at 21 45 10](https://user-images.githubusercontent.com/53974876/149835478-2a50f3e8-8cb6-40d4-94ba-e896d7501c13.jpeg)



Now, let's block the access to control panel, On the policy editor window, the setting that we’re looking for is under User Configuration > Adminsitrative Templates > Control Panel , find one setting named `Prohibit access to Control Panel and PC settings`.


We make sure it is set to `Enabled`.

![Capture d’écran 2022-01-17 214713](https://user-images.githubusercontent.com/53974876/149835318-b26b6444-7a18-4ca2-ba4f-a6cb19d55f6a.png)

Now we need to apply the settings by the following command `gpupdate /force`


![win](https://user-images.githubusercontent.com/56129562/149037875-b81ce129-5b5a-4d6e-a6f7-1ceecc302200.png)

As a last step, we need to link the user to the GPO:

![WhatsApp Image 2022-01-17 at 21 20 52](https://user-images.githubusercontent.com/53974876/149835550-b325efee-adc4-457a-bc47-b3103864814d.jpeg)

Results When trying to access control panel, or Windows Settings, we get the following error.

![wi](https://user-images.githubusercontent.com/56129562/149038024-7c51e574-4f24-40f5-a864-121c6962c9c1.png)



