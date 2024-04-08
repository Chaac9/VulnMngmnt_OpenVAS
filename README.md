# Vulnerability Management using OpenVAS

## Introduction

Using the Azure cloud platform, I created and configured two virtual machines, one to use OpenVAS and conduct vulnerability scanning and vulnerability management, and another to be used as an exposed and insecure virtual machine from which vulnerabilities would be recorded. The insecure virtual machine was misconfigured with insecure security settings and had outdated software from which the vulnerability scanner detected and recorded weaknesses and flaws in the system. By using OpenVAS I can detect and mitigate exposures and potential attack vectors, with greater details being obtained by OpenVAS records when credentials of hosts are provided within the vulnerability scans.  


## Architecture of the Computers tied to the Vulnerabiility Scan and OpenVAS:
-  Virtual Machine 1 (Uses OpenVAS)
    -  Connection to OpenVAS by SSH is done through a terminal of the virtual machine providing credentials and a web link from which we will sign into the OpenVAS vulnerability management application through a web browser.      
-  Virtual Machine 2 (Insecure Windows 10 Host)
    -  Outdated and deprecated software downloaded
        - Adobe Reader X
        - Firefox
    - Misconfigured Security Settings
        - Disabled Firewall Settings

## Connecting to the OpenVAS web-app 

When creating your server (virtual machine) and configuring your vulnerability management scanning software, take note of the credentials used to login to your machine as we will use a terminal to connect to the device through using the ssh command, the username, and public IP address to the device. 

The 2 images provided below show my ssh connection to the virtual machine acting as the OpenVAS server:
  - The public IP address of this virtual machine is no longer in use as the resource has been deleted
    
![image](https://github.com/Chaac9/VulnMngmnt_OpenVAS/assets/98796264/40f1e1a6-a94b-42e0-b6cf-046575e50c9d)

  - A web-link to the OpenVAS application and the credentials used to login are provided.
      - These credentials no longer work as the server is no longer in service
         
![image](https://github.com/Chaac9/VulnMngmnt_OpenVAS/assets/98796264/7c099753-8f0d-4a35-b108-12632332fefb)

## Implementing Insecure Controls and Exposing the Windows Vulnerable Virtual Machine 

The first step to exposing the host is disabling firewall states for all profiles:
  - Within the Virtual Machine's search bar, search for 'Windows Defender Firewall'
      -  Select the 'Advanced settings' option and then the 'Windows Defender Firewall Properties' to disable the firewall for all properties
      -  Within each profile disable the firewall state, and then apply changes after configurement is completed

![image](https://github.com/Chaac9/VulnMngmnt_OpenVAS/assets/98796264/ec5247aa-12e6-4318-acdd-feee0b51afcc)

## Metrics of an Unauthenticated Scan using OpenVAS

An unathenticated scan will not use credentials to access a system and will rely on network-based techniques to provide a broader view of potential vulnerabilties that may not be as acurate or comprehensive as authenticated scans. 

| Metric                   | Count
| ------------------------ | -----
| Results                  | 34
| Applications             | 0
| CVE                      | 2
| Closed CVEs              | 7
| TLS Certificates         | 0

## Metrics of an Authenticated Scan using OpenVAS

An Authenticated scan in OpenVAS involves the use of credentials to access the target device to perform the scan providing deeper insight and more accurate information within records. Ensure you implement high security controls when using credentials within the OpenVAS web application as it is a high security risk. 

| Metric                   | Count
| ------------------------ | -----
| Results                  | 85
| Applications             | 17
| CVE                      | 29
| Closed CVEs              | 3889
| TLS Certificates         | 1

## Conclusion

This project involved the use of a vulnerable host that would be scanned for vulnerabilities and weaknesses by the OpenVAS web application. The vulnerable host had outdated software downloaded and security controls like the built-in firewall disabled. Multiple vulnerability scans, an authenticated and unauthenticated scan, were conducted and reported different results in their recorded vulnerabilities and weaknesses of the target host. As shown by the metrics reported from the scans, an authenticated scan may have improved coverage into the insight of the weaknesses for a device. Despite the advantages of scans that use credentials to login, such as having more accurate results or better remediation guidance, it is essential to implement strong security controls and cybersecurity awareness where credentials may be stored. 
