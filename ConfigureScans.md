# OpenVAS Scan Configurement for Authenticated and Unauthenticated Scans

## Introduction
Configuring OpenVAS to scan the private IPs of devices within our network allows us to view reports of vulnerabilities, such as from operating systems, web applications, and network services like email or web servers. The configurement of an unauthenticated (simple) and an authenticated scan is done as simple scans only scan using the network, while authenticated scans also survey for weaknesses internally within the system. For the Authenticated scan we will use SMB credentials, being the username and password of the target, as I will be scanning a Windows 10 virtual machine.

## Configuring a Simple Scan

The first step of configuring a simple scan is to create a target. 
  - On the OpenVAS (GreenBone) web application platform, we will first select the "Configuration" Tab > and then the "Targets" option
  - We will then select the icon that is a block with a star in the corner, located near the top right of the web application under the "Dashboard" category, to create a new targert
  - Afterwards we will name the Target (Windows 10 VM) and input the private IP address under the Manual option of the Hosts category. 


We will then create a task, as tasks are used to control the executions of scans
  - Select the "Scans" category andthen selec the "Tasks" option 
  - Then select the same icon located under the "Dashboards" category that has a star on the corner of the block icon 
  - When configuring our tasks, select the target recently made in the first step
      -- We will select default options when creating the new task, but there are several other options such as Alerts and Schedule
      -- Alerts allows the user to send changes found within scans to an email, syslog, or other connectors 
      -- The Schedule option alows for scans to be run on a schedule, such as every Wednesday at 10:00 a.m. 

After we have configured our task to select our target device, we will execute the task, as so it creates a report of the vulnerabilities it discovered
  - To execute the scan, Ensure you're on the "Tasks" page under the "Scans" category 
  - You should see your newely created task near the bottom of the page, select the "Start" option under the "Actions" category. 


## Configuring an Authenticated Scan

We will now add credentials for our authenticated scan to allow the vulnerability scanner to login into the devie and perform the internal scan
  - Select the "Configurations" option and then the "Credentials" option 
  - We will select the same icon used to create objects as the other devices locate under the "Dashboard" categoery
  - Provide a name, for the type select "Username + Password," and input the Username and password of the target device usedd to login
      -- Select "No" for the "Allow Insecure use" and the "Auto-generate" options

we will now configure a new target, which will use the SMB credentials to login
  - Under the first target created, we can select the sheep icon under the "Actions" category, as it will allow us to clone our recently created target and ensure we can make the small configurations needed for our latest authenticated scan
  - We will then select the "Edit Target" option under the "Actions" category and make the changes needed under the "Credentials for authenticated checks" 
  - In the "SMB" category we will selecct the credentials recent made under "Configurations" > "Credentials." 
  - Save the changes made

The last step is to create and  execute the newly cloned authenticated scan which will now use our newly configured cloned target that uses the SMB credentials 
  - We will select the clone option under the "Actions" category 
  - In the "Scan Targets" option select the newly cloned target which contains the SMB credentials to your device
  - Select the "Start" button under the "Actions" category 

## References
https://docs.greenbone.net/GSM-Manual/gos-22.04/en/scanning.html#configuring-a-simple-scan-manually
https://docs.greenbone.net/GSM-Manual/gos-22.04/en/scanning.html#authenticated-scan
https://docs.greenbone.net/GSM-Manual/gos-22.04/en/scanning.html#configuring-an-authenticated-scan-using-local-security-checks
https://docs.greenbone.net/GSM-Manual/gos-22.04/en/scanning.html#using-credentials