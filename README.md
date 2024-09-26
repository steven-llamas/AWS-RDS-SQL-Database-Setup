


<h2>Description</h2>
<p>This tutorial demonstrates how to use Amazon Web Services (AWS) and set up a Relational Database Service (RDS), enabling seamless access to an SQL database from anywhere with an internet connection. You will learn how to navigate AWS RDS services and familiarize yourself with hosting a database in the cloud. By the end of this guide, you'll know how to configure and connect to an RDS instance securely, providing global access to your database. This tutorial will also show you how to connect to the AWS database using SQL Server Management Studio (SSMS), Microsoft's SQL database platform.</p>


<h2>Applications Used </h2>

- <b> <a href="https://www.microsoft.com/en-us/sql-server/sql-server-downloads">Microsoft SQL Server </a></b>
- <b> <a href="https://aws.amazon.com/rds/">Amazon RDS</a></b>

<h2> Tutorial Portion</h2>

<p align="center">
Go to the AWS RDS webpage and create an account or sign in. For ease of use, a hyperlink to the webpage is included in this tutorial. Next, go to the search bar and search for RDS.</p>
<div align="center">
  <img src="https://i.imgur.com/LEC5hbg.png" height="80%" width="80%" alt="Amazon RDS Website."/>
  <img src="https://i.imgur.com/Kjnnztk.png" height="80%" width="80%" alt="Choosing the right download link."/>
</div>
<br />

<p align="center">
Once on Amazon RDS, click <b>Create Database</b>. On the new webpage, Click on <b>Easy create</b>, so that best practices will be used and the DB will be overall simpler to set up. Next, for the <b>Engine Options</b> select <b>Microsoft SQL Server</b>. After choosing the Engine Option, we will be selecting which <b>DB instance size</b> to use, for this example I will be using the <b>Dev/Test</b>. Choose the correct DB instance for what you will be using the DB. Next is the <b>DB instance identifier</b>, which is the name of the DB, this can be the default "database-1". The <b> Master username </b> is the login ID name for the admin of the DB, set it as something that you can remember such as "admin_s". Next is <b>Credentials management</b>, which gives you options on how to handle the master password. In this tutorial we will create a <b>Master password</b>. Set this password to something you can remember. After all the changes have been made, click on <b>Create database</b>, and wait approximately 10-15 minutes for the database to be created. </p>
<div align="center">
  <img src="https://i.imgur.com/eETOwan.png" height="80%" width="80%" alt="Clicking on Create Database."/>
  <img src="https://i.imgur.com/6Awhs4u.png" height="80%" width="80%" alt="Choosing Easy create and choosing Microsfot SQL Server."/>
  <img src="https://i.imgur.com/JSFNCbP.png" height="80%" width="80%" alt="Showing the rest of the options when creating a Database."/>
  <img src="https://i.imgur.com/o1mTjG6.png" height="80%" width="80%" alt="Clicking on 'Create Database'."/>
  <img src="https://i.imgur.com/uyT6Rz0.png" height="80%" width="80%" alt="Showing the database instance creating."/>
</div>
<br />
<p align="center">After our database state is shown as <b>Available</b>, we will now make the database accessible publicly. Select the database and click on <b>Modify</b>. Once on the new page, scroll down till you see the subtitle <b>Connectivity</b>. Then click on <b>Additional configuration</b> and select <b>Publicly accessible</b>. After such actions, click on <b>Continue</b> and within the <b>Schedule modifications</b> select <b>Apply Immediately</b> and select <b>Modify DB instance</b>.</p>
<div align="center">  
  <img src="https://i.imgur.com/NUVqaXA.png" height="80%" width="80%" alt="Modifying the database."/>
  <img src="https://i.imgur.com/gxTqMHD.png" height="80%" width="80%" alt="Setting the database to publicly accessible."/>
  <img src="https://i.imgur.com/eRLESYC.png" height="80%" width="80%" alt="Selecting 'Continue'."/>
  <img src="https://i.imgur.com/KhHLo1G.png" height="80%" width="80%" alt="Clicking on 'Modify DB instance'."/>
</div>
<br />
<p align="center">Next we will configure Security Groups (the set of rules for the firewall). To begin, click on the <b>DB identifier</b>. Next, make sure you are on the <b> Connectivity & security </b> section. Once there, click on the link under the <b>VPC security groups </b>. In the <b>Security Groups</b> click on the security group, once clicking on the group a tab will open on the bottom of the page where you will click on <b>Inbound rules</b>. Next, click on <b>Edit inbound rules</b>. Once there, select <b>Add rule</b>, a new row will pop up where in the type section, select <b>MYSQL</b>. Within the <b>Source</b> you will have the option to either input your computers IP address, so that only your computer will be able to access the DB, or selecting <b>Anywhere-IPv4</b> so that when using a hotspot or when using another ISP you are able to access the DB. Finally, select <b>Save rules </b>. </p>
<div align="center">
  <img src="https://i.imgur.com/C1aKoyb.png" height="80%" width="80%" alt="Clicking the 'DB identifier'."/>
  <img src="https://i.imgur.com/FThIsMp.png" height="80%" width="80%" alt="in 'Connectivity & security, clicking VPC security groups."/>
  <img src="https://i.imgur.com/fagVOXU.png" height="80%" width="80%" alt="Within 'Security Groups' going to 'Inbound rules' ."/>
  <img src="https://i.imgur.com/5gTgd0N.png" height="80%" width="80%" alt="editing the inbound rules."/>
  <img src="https://i.imgur.com/RBBZ56N.png" height="80%" width="80%" alt="Adding a rule within the Inbound rules."/>
<br />
  
<p align="center">After these changes, what is next is to download <b>SMSS</b> if you have not already. I have added the link to Microsoft's website to download the application. Once downloaded, open the application. Then go back to the amazon RDS website and click on the database instance again and select <b>Connectivity & security</b>, once there copy the <b>Endpoint & port</b> information. Next you need to locate your <b> Master username and Master password</b> to sign in, if you forgot you can go to the <b>Configuration</b> to see your <b>Master Username</b>. After having all this information, go back to <b>SMSS</b> and make sure you are on the <b>Login</b> tab. once there you will input your endpoint name and port after using a <code>,</code> in the <b>Server name</b> section, for example <code>database-2.************.*********.rds.amazonaws.com,1433</code>. For authentication, you will select <b> SQL Server Authentication</b>. For the <b>Login</b> section you will input your <b>Master password</b> that you have created, as well as your <b>Master password</b> within the <b>Password section</b>. Make sure <b>Trust server certificate</b> is checkmarked; otherwise, you will not be able to access the database. Select <b>Connect</b> and wait for the database to connect. Once connected successfully, you will be able to see all the folders within the database. </p>
<div align="center">
  <img src="https://i.imgur.com/PvuPinx.png" height="80%" width="80%" alt="Showing how MSSMS looks like."/>
  <img src="https://i.imgur.com/q09t3XB.png" height="80%" width="80%" alt="Showing what sections to copy."/>
  <img src="https://i.imgur.com/AtiWYLS.png" height="80%" width="80%" alt="Showing the Configuration tab."/>
  <img src="https://i.imgur.com/edTTtQj.png" height="80%" width="80%" alt="Showing how to login to SMSS."/>
  <img src="https://i.imgur.com/Hoybtxj.png" height="80%" width="80%" alt="Showing how the database looks like."/>
</div>
<br />

<h2>Additional Information: Creating Databases in SMSS</h2>

<p align="center">To create a new database within the AWS RDS Instance, right click on <b>Databases</b> and select <b>New Database...</b>. A new window will appear, type in the name of the database in <b>Database name:</b> and select <b>OK</b>. Next, click on your new database to select it and then click on <b>New Query</b> to begin modifying the DB using <code>SQL</code> commands. Now with the Query tab open, you are now able to create tables. For this example, I will create a table called <b>Employees</b> with columns: <b>EmployeeID, FirstName, LastName, Department, & HireDate</b>. Here is the following code for the Employee table.<code> CREATE TABLE Employees (EmployeeID INT IDENTITY(1,1) PRIMARY KEY, FirstName NVARCHAR(60) NOT NULL, LastName NVARCHAR(60) NOT NULL, Department VarChar(50), HireDate DATE NOT NULL );</code>. The <b>EmployeeID</b> is set as the <code>PRIMARY KEY</code>, as this column is going to have the values that uniquely identify the table. This column is to only have data type <code>INT</code> or Integer values (...-2,-1,0,1,2...), as well as <code>IDENTITY(1,1)</code>, this allows that each employee has an automatic EmployeeID, starting with 1 and increasing by 1. The <b>FirstName</b> column, as well as the <b>LastName & Department</b>, use the <code>NVARCHAR</code> data type. This datatype is a variable character datatype, which means the column can be filled with up to the amount of characters within the argument, so <code>NVARCHAR(60)</code> allows up to 60 characters in the column. Lastly, for <b>HireDate</b>, the data type is <code>DATE</code>, which means the data in this column is in the data format <b>YYYY-MM-DD</b>. Also, the <code>NOT NULL</code> constraint means that the column MUST be filled when inserting or making changes to the table. After typing in the code, click on <b>Execute</b>. Once executed, a tab will pop up showing whether the commands were completed successfully. To insert values into the database, you can use the <code>INSERT INTO</code> command, where you type the table you want to insert the values, the columns you want to insert, in order of how you created the table. Here is an example of inserting values <code>INSERT INTO Employees (FirstName, LastName, Department, HireDate) VALUES ('Josh', 'Doe', 'Marketing', '2023-01-15'), ( 'Jane', 'Smith', 'Sales', '2023-03-23');</code>. To check the tables values you can use <code>SELECT * FROM Employees;</code>, where the <code>*</code> is a wildcard and basically means to select ALL from the table Employees, this shows you the table at the bottom of the app. Since I accidentally added copies of the employees, I will use the command <code>DELETE FROM Employees WHERE EmployeeID IN (3, 4);</code> which will remove the typos. After this command you can use <code>SELECT * FROM Employees;</code> to show the table again. </p>
<div align="center">
  <img src="https://i.imgur.com/O96xJka.png" height="80%" width="80%" alt="Creating a new Database in SMSS."/>
  <img src="https://i.imgur.com/XHSzUq9.png" height="80%" width="80%" alt="Naming the database and finalizing creation."/>
  <img src="https://i.imgur.com/IWiYlK6.png" height="80%" width="80%" alt="showing how to open the query."/>
  <img src="https://i.imgur.com/DgwqDjt.png" height="80%" width="80%" alt="Creating a Table in the Database."/>
  <img src="https://i.imgur.com/yxHHNee.png" height="80%" width="80%" alt="Showing the command completed successfully."/>
  <img src="https://i.imgur.com/2P4vGPK.png" height="80%" width="80%" alt="Showing the code to insert a command."/>
  <img src="https://i.imgur.com/Ty6tNF8.png" height="80%" width="80%" alt="Showing the table."/>
  <img src="https://i.imgur.com/9TmNYY3.png" height="80%" width="80%" alt="Showing the changes to the table."/>
</div>
