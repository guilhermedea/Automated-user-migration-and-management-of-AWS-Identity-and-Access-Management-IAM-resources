# Automated user migration and management of AWS Identity and Access Management IAM resources


![postpicture](https://miro.medium.com/v2/resize:fit:720/format:webp/1*Pr78CMgUIOC2px6rFws54g.png)

In this project based on a real-world scenario, I acted as Cloud Specialist with the mission to migrate users in an automated way and manage AWS IAM 
(Identity and Access Management) resources.

There were 100 users that needed to be migrated and have MFA (Multi-factor authentication) enabled on their accounts, as this is a security best practice.

![soluction architecture](https://miro.medium.com/v2/resize:fit:720/format:webp/1*-RTS0j52RzHKrwWtakcSrw.png)

To avoid repetitive and manual tasks in the AWS console, I needed to think about automating the processes and using the available tools.

The first step was organizing the already available data, which was a table with names, emails and already existing groups. Using a simple search and replace, 
the data was quickly adapted, so I could use them with a script that automated account creation on AIM.

The second step was to prepare AIM to receive the new users. Trough the console, five user group were created (NetworkAdmins, LinuxAdmins, CloudAdmins, 
DBAs and Interns), each one with its own access policies. A custom policy was created to enforce MFA for all accounts,
locking basic functions until the user has activated it.

![One of the user groups, with its own access policy](https://miro.medium.com/v2/resize:fit:720/format:webp/0*yfb3KA9XxioNuOSB.png)

With the IAM ready to receive the new users, it was necessary to setup the CloudShell to run the automation script. Using GitBash with the AWS CLI, I connected to 
the CloudShell and installed the required library to run the script (Dos2Unix). Preparations done, I opened the script on Visual Studio Code, to make sure it was
correctly configured, as was the data table with the user accounts.

With all the resources ready, I ran the script and the accounts were automatically created, already distributed trough the user groups with its own access policies.

![The script creating the user accounts on AIM.](https://miro.medium.com/v2/resize:fit:720/format:webp/0*_7MTvw5LrX8x0RSz.png)

After the accounts were created, I proceeded to the verification tests. I logged on two accounts to check the access. Initially I had a problem with the MFA enforcement 
policy: the system didn’t allow the user to add its own device, even with the policy explicitly allowing that. To solve the problem I remade the policy using a template
available on the AWS documentation. After that correction, the users were able to correctly activate their MFA devices and access their resources without problems.

![The users table, showing MFA activated for all users. For practical reasons, only four users were created.](https://miro.medium.com/v2/resize:fit:720/format:webp/0*keA-ai9jz4CBDECD.png)

The implementation process of this project highlighted important values, showing that organization and practice are as critical as technical skills to quickly resolve 
problems. Also, it’s possible to see how quickly problems can be solved trough automation, which brings a much more dynamic and quick workflow to the client
and to the specialist.
