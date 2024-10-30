<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial will outline the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure 
- Remote Desktop
- Internet Information Services (IIS)
- HeidiSQL

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Project Walk-through</h2>

<p align="center">
To begin, we'll use Microsoft Azure to set up a Virtual Machine (VM) for building osTicket from scratch. This VM setup protects our personal computers from potential issues. Start by creating a "Resource Group" in Azure, naming it "osTicket," then create a VM with 2-4 vCPUs.
<br/>


![Screenshot 2024-09-25 210900](https://github.com/user-attachments/assets/a6cede58-ee0e-4104-90c7-3a105f16fa14)

<br/>


<p align="cneter">
Next, connect the new VM to your personal computer via RDP. Mac users should download the RDP client from the App Store beforehand.
<br/>

![Screenshot 2024-09-25 211704](https://github.com/user-attachments/assets/40e876ae-1cbf-4945-92ac-a7ad139a0d49)

<br/>

<p align="center"> 
Once connected to the VM, install and enable IIS (Internet Information Services). Navigate to Control Panel > Programs > Turn Windows Features On or Off, enable Internet Information Services, then expand "World Wide Web Services." Under "Application Development Features," enable CGI.
  <br/>


![image](https://github.com/user-attachments/assets/6ae20913-04a6-45e4-baf9-cdaffc964009)

<br/>

<p align="center"> 
Install PHP manager for IIS setup 
<br/>

![Screenshot 2024-09-26 005747](https://github.com/user-attachments/assets/ce927ca7-6eaf-4ea9-97ff-052664a5b0c6)

<br/>

<p align="center">
Install IIS Rewrite Module
<br/>

![Screenshot 2024-09-26 005834](https://github.com/user-attachments/assets/4b261216-fd0c-49f8-bc05-18c3e526934f)

<br/>

<p align="center">
Once the installations are complete, create a PHP directory on the C drive.
  <br/>

![Screenshot 2024-09-26 010053](https://github.com/user-attachments/assets/dd313999-6911-4807-a196-592d1c6ddfcc)

<br/>

<p align="center">
Download PHP and extract the zip file into the PHP directory you just created.
<br/>

![Screenshot 2024-09-26 010259](https://github.com/user-attachments/assets/f8dcdf73-c9cd-4819-a9d9-b5c09494399f)

<br/>

<p align="center">
Install Microsoft Visual C++
<br/>

![Screenshot 2024-09-26 010458](https://github.com/user-attachments/assets/1323af5f-e106-41e0-997d-a2544739de75)

<br/>

<p align="center">
Install MySQL

<br/>

![Screenshot 2024-09-26 010639](https://github.com/user-attachments/assets/a08c80d2-4053-46f5-a080-6257e87edc08)

<br/>

<p align="center">
Next, create login credentials and store them securely, as the password will be needed later.

<br/>

![Screenshot 2024-09-26 010824](https://github.com/user-attachments/assets/19f51d9d-2b20-4efe-961f-a3b5ff912f3c)

<br/>

<p align="center">
Open IIS as an Administrator 
<br/>

![image](https://github.com/user-attachments/assets/efd7af45-3c05-494f-af82-98b472bba129)

<br/>

<p align="center">
Navigate to PHP manager and selecet "Register new PHP version". There should be a "php-cgi.exe" file that appears. Select it!
<br/>

![image](https://github.com/user-attachments/assets/ee50cd90-89c6-40ce-84af-1bc337df06b8)
![image](https://github.com/user-attachments/assets/074f53a0-7f60-43bf-8dd0-c70aa5d74822)

<br/>

<p align="center">
 Under IIS, Select the osTicket VM and select "Restart" under Manage Server
<br/>

![image](https://github.com/user-attachments/assets/c0902483-0b3b-4f8a-9049-3d66a1691f9e)

<br/>

<p align="center">
Download osTicket and copy the upload file to wwwroot file in the inetpub file

<br/>

![Screenshot 2024-09-26 011958](https://github.com/user-attachments/assets/f9feb4f2-4317-4219-87ed-3b06aee7ce46)

<br/>

<p align="center">
Rename the file "osTicket"

<br/>

![image](https://github.com/user-attachments/assets/0bb767f9-84ea-4a36-b8a9-0c2b68793298)

<br/>

<p align="center">
Return to IIS and restart the serve. Next select *80 (http) 
<br/>

![image](https://github.com/user-attachments/assets/205c2ef6-f94b-4d3e-8b34-ce95539a08f4)

<br/>

<p align="center">
This page will open. The red "X's" indicate the extensions that aren't enabled 
<br/>

![Screenshot 2024-09-26 013049](https://github.com/user-attachments/assets/8f0ccf2e-aca3-4766-9f11-52fae724d724)

<br/>

<p align="center">
Navigate over to IIS> Sites> Default Web Site> osTicket. Seleect PHP manager> Enable : php_imap.dll, php_intl.dll, php_opache.dll
<br/>

![image](https://github.com/user-attachments/assets/2952e9f2-055a-4207-b1a7-3e9506f99c7f)
![image](https://github.com/user-attachments/assets/300e0670-3d41-430e-8554-8e3bba62fcc3)

<br/>

<p align="center">
Afte enabling the PHP extenions. We can observe the changes 
<br/>

![Screenshot 2024-09-26 013818](https://github.com/user-attachments/assets/da0a12f9-1c65-45ce-8c58-bfc720df4983)

<br/>

<p align="center">
Browse over to file explorer > C drive> osTicket> include> ostsampleconfig.php. Next we're going to remove the "sample" from the file name
<br/>

![image](https://github.com/user-attachments/assets/09d8a0db-0dc3-4176-bb08-3da861dc30c5)

<br/> 

<p align="center">
Right-click on ost-config.php, select Properties > Security > Advanced. Choose Disable Inheritance and Remove all inherited permissions from this object. Click Add, enter Everyone, select Check > OK, check Full permissions > OK > Apply > OK.
  
<br/>

![Screenshot 2024-09-26 014427](https://github.com/user-attachments/assets/d659e04a-8f75-445a-94ba-8ddcce07f08e)

<br/>

<p align="center">
Continue on the osTicket web page and fill out the set up page
<br/>

![Screenshot 2024-09-26 014619](https://github.com/user-attachments/assets/8477c6d0-1f99-4078-8a7f-46ad8cdd7464)

<br/>

<p align="center"> 
Install HeidiSQL
<br/>

![Screenshot 2024-09-26 014845](https://github.com/user-attachments/assets/ca330376-a685-42c6-96c5-a3cb88106bf0)

<br/>

<p align="center"> 
After installation, select New, enter Username: root, and use the MySQL password set up earlier. Click OPEN. On the left side, right-click unnamed and create a new database named osTicket.
  
<br/>
  
![image](https://github.com/user-attachments/assets/dca9c043-e43a-4420-bd56-56162a5f895c)
![Screenshot 2024-09-26 015836](https://github.com/user-attachments/assets/1b151c48-2c59-49ee-a61e-3fc11b46bd4a)

<br/>

<p align="center">
Select Install and you should recieve a "Congratulations" from osTicket
<br/>

![Screenshot 2024-09-26 020103](https://github.com/user-attachments/assets/5a45773f-6dec-487f-907f-b23901c8db1b)
![Screenshot 2024-09-26 020240](https://github.com/user-attachments/assets/ad08dafe-fe27-4758-bea5-6d26168610d5)
