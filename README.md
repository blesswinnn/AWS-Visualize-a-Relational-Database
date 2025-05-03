# AWS-Visualize-a-Relational-Database
The goal of this project is to set up our own relational database and visualize it using some charts all using AWS.

![image](https://github.com/user-attachments/assets/bfe10f71-6816-4d12-89cb-8e6fa4257b51)

# Login with your IAM user

![image](https://github.com/user-attachments/assets/182d0326-164a-4f23-8a24-f8e628a1221d)

# Create a Relational Database

Head to your RDS console - search for rds in search bar at the top of the screen.


![image](https://github.com/user-attachments/assets/c2ccd75e-c792-415d-95b0-c3a71af45f9b)

- In the left navigation bar, select Databases.
- In the Database section, select Create Database.
- On the Create database page, choose Easy Create.
- In the Configuration section, make the following changes:
- For Engine type, choose MySQL.
- For DB instance size, choose Free tier.

![image](https://github.com/user-attachments/assets/fbeb6a6b-f580-46d1-9b9b-5189bd423b57)

- For DB instance identifier, type QuickSightDatabase.
- For Master username, enter admin.
- In the Credentials management section, select Self managed
- For Master password, type a unique password, and confirm password.
- Make sure you save your database login details somewhere safe! You'll need them later on.

![image](https://github.com/user-attachments/assets/bac7dad3-e78b-464b-a46e-77c6d13a37b5)

- Leave the rest as the default settings and select choose Create database.

# This is what we created in this step:
![image](https://github.com/user-attachments/assets/dfd9cdc0-8916-4d0e-837a-885e15cb9362)

![image](https://github.com/user-attachments/assets/7ef270aa-6d13-4baf-856d-76c6a5957051)

# Connect RDS to MySQL Workbench :
- Download MySQL Workbench
- Make your RDS instance public, to allow connections from outside the AWS network (ie. from our local machine using 
  MySQL Workbench)
- Modify the security group attached to your RDS instance so that your local machine can access your RDS instance.
- Connect MySQL Workbench to your RDS.
![image](https://github.com/user-attachments/assets/a36cc4cd-609e-4ad5-a8bd-3b6c7e65f320)

- my SQL DOWNLOAD LINK :  https://dev.mysql.com/downloads/workbench/

# Make your AWS database public so we can connect it to MySQL Workbench
- Open the Amazon RDS console, in the left-hand navigation pane, choose Databases.
- Then, choose QuickSightDatabase.
- On the QuickSightDatabase page, choose Modify.
- Scroll down to the Connectivity section, choose Additional Configuration.
- Then, choose Publicly accessible.
![image](https://github.com/user-attachments/assets/88b381f1-9964-4728-9068-2027d427fa5d)
![image](https://github.com/user-attachments/assets/50bfcb46-9d8c-47d7-8089-e84d56ffad1a)
- Choose Continue.
- Choose Apply immediately.
- Select Modify DB instance.
![image](https://github.com/user-attachments/assets/6dd63b66-f55f-4177-8ce8-9833b92e8668)
![image](https://github.com/user-attachments/assets/34204036-f2dc-4c0b-ab2c-2c270036f450)

# 

![image](https://github.com/user-attachments/assets/b4245a0b-bad2-478e-a5ff-0a88cab47af6)

# Modify the security group attached to your RDS instance

- Next we want to modify the security group attached to your RDS instance so that your local machine can access your 
  RDS instance.
- In Amazon RDS in your AWS console, go to the left-hand navigation, and select Databases.
- Then, choose quicksightdatabase.
- On the quicksightdatabase page, in the Connectivity & security section, choose the VPC security groups link.

![image](https://github.com/user-attachments/assets/48750e22-7220-4608-be53-35360481debd)
- On the sg-default page, in the Inbound rules section, choose Edit inbound rules.
- On the Edit inbound rules page, in the Inbound rules section, choose Add rule, and make the following changes:
- For Type, choose All TCP from the drop-down list.
- For Source, choose My IP.
- Then, choose Save rules.
![image](https://github.com/user-attachments/assets/9048e2f1-486f-4f0f-8234-56e9f745b282)

![image](https://github.com/user-attachments/assets/6199ee28-5320-4a97-9414-49a557c2095d)
# Login to your Database from MySQL Workbench
- Select Databases in the top menu bar, then Manage Connections...
- Select New in the bottom left.
  ![image](https://github.com/user-attachments/assets/fe0bc451-de8b-48b4-bc42-c9e8e67460a0)
![image](https://github.com/user-attachments/assets/a56d9e2a-4648-41c0-9017-99527784184f)

- Enter the following details:
  - For Connection Name, paste AWS-QuickSightDatabase
  - For Hostname, return to your RDS database page for your QuickSightDatabase.
- Look under Connectivity and security to find the Endpoint.
- Example: QuickSightDatabase.abc.us-east-1.rds.amazonaws.com,1433
- Copy this into Hostname in your MySQL Workbench.
- Copy the Port from the same place in AWS to the Port field in MySQL Workbench.
![image](https://github.com/user-attachments/assets/9642c227-6d2d-4029-8857-92bef11f64a4)
![image](https://github.com/user-attachments/assets/3f267a12-b885-41f5-acba-fc7e918b4546)
- For Username, type the username you entered when creating the QuickSightDatabase (probably admin unless you changed it).
- For Password, select Store in Keychain ... then enter in your database password.
- Then, choose Test Connection.
- You should get a pop-up that say's Successfully made the MySQL connection. 
![image](https://github.com/user-attachments/assets/2ddb1cd6-bf58-4404-840b-e66064ad58e3)

# Create Database Tables and Load Data:
- Create a new schema using MySQL Workbench
- Create two new tables in your schema
- Populate those tables with data using SQL

- Select Schemas as the tab in the top left, next to Administration.
- Right click on the blank space under the Schemas menu.
- Select Create Schema.
![image](https://github.com/user-attachments/assets/c97ef873-b22e-45b9-962f-e3d9c9bccb52)
- Name your schema QuickSightDatabase
- Leave everything else as is, and select Apply.
# In your new Query script, copy and paste the following SQL query:
    CREATE TABLE newhire(
    empno INT PRIMARY KEY,
    ename VARCHAR(10),
    job VARCHAR(9),
    manager INT NULL,
    hiredate DATETIME,
    salary NUMERIC(7,2),
    comm NUMERIC(7,2) NULL,
    department INT)

![image](https://github.com/user-attachments/assets/b4f2f5cb-8c9e-4079-b0d0-826dcc1dfbb1)

- Run your Query script by selecting the lightning button above your script.

- To see the results from our query, delete the current query and replace it with the following:

        SELECT * FROM newhire;
![image](https://github.com/user-attachments/assets/744869e3-694f-4b19-9420-7761d0a22afa)
- Now let's populate our new table by running another query.
- Delete the current contents of your query script and paste in the following

      INSERT INTO newhire (empno, ename, job, manager, hiredate, salary, comm, department) VALUES
      (1, 'JOHNSON', 'ADMIN', 6, '1990-12-17', 18000, NULL, 4),
      (2, 'HARDING', 'MANAGER', 9, '1998-02-02', 52000, 300, 3),
      (3, 'TAFT', 'SALES I', 2, '1996-01-02', 25000, 500, 3),
      (4, 'HOOVER', 'SALES I', 2, '1990-04-02', 27000, NULL, 3),
      (5, 'LINCOLN', 'TECH', 6, '1994-06-23', 22500, 1400, 4),
      (6, 'GARFIELD', 'MANAGER', 9, '1993-05-01', 54000, NULL, 4),
      (7, 'POLK', 'TECH', 6, '1997-09-22', 25000, NULL, 4),
      (8, 'GRANT', 'ENGINEER', 10, '1997-03-30', 32000, NULL, 2),
      (9, 'JACKSON', 'CEO', NULL, '1990-01-01', 75000, NULL, 4),
      (10, 'FILLMORE', 'MANAGER', 9, '1994-08-09', 56000, NULL, 2),
      (11, 'ADAMS', 'ENGINEER', 10, '1996-03-15', 34000, NULL, 2),
      (12, 'WASHINGTON', 'ADMIN', 6, '1998-04-16', 18000, NULL, 4),
      (13, 'MONROE', 'ENGINEER', 10, '2000-12-03', 30000, NULL, 2),
      (14, 'ROOSEVELT', 'CPA', 9, '1995-10-12', 35000, NULL, 1);

- To see the results from our query, delete the current query and replace it with the following:

        SELECT * FROM newhire;

![image](https://github.com/user-attachments/assets/89d341ca-ea20-41e7-acbe-a3460812852d)

# Remove the current query and run the following to create and populate a second table:

      CREATE TABLE department(
      deptno INT NOT NULL,
      dname VARCHAR(14),
      loc VARCHAR(13));

     INSERT INTO department (deptno, dname, loc) VALUES 
     (1, 'ACCOUNTING', 'ST LOUIS'),
     (2, 'RESEARCH', 'NEW YORK'),
     (3, 'SALES', 'ATLANTA'),
     (4, 'OPERATIONS', 'SEATTLE');

- To see the results from our query, delete the current query and replace it with the following:

        SELECT * FROM department;
![image](https://github.com/user-attachments/assets/b0222a5d-f9bf-4364-86ef-862ae3437b00)


# Connect RDS to QuickSight
- Adjust the security group attached to our RDS instance to allow inbound requests from QuickSight.
- Add your RDS instance as a data source in QuickSight.

- Navigate back into your RDS instance from the RDS console in AWS.
- Open your RDS instance.
- Under Connectivity & security, select the link in VPC security groups to open the related security group.
- Open the security group by selecting the Security group ID
- Select Edit inbound rules to add a new rule with the following details:
  Type: All Traffic , Source: Custom, then 0.0.0.0/0 in the next box





