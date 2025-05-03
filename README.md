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

![image](https://github.com/user-attachments/assets/359d2435-6c66-4c0c-a32e-1aa162ff7858)
- Select Save rules
- Navigate to QuickSight by searching Amazon QuickSight in the search bar at the top of your AWS console.
- If this is your first time using QuickSight, follow the sign-up flow;
- PLEASE make sure to untick the offer to upgrade with the optional add-on Add Paginated Reports. No getting charged 
   today!
- Make sure you select the same Region as the one you've been doing this project in.

![image](https://github.com/user-attachments/assets/0d1733a6-5ace-4a81-a7d3-de1119e8178a)

![image](https://github.com/user-attachments/assets/d12f324b-0b09-47b3-8789-e081d32f9ec5)
- Once you're in QuickSight, select Datasets from the left menu.
- In the top right of the screen, select New dataset
- select RDS
- Fill out the following values:
- Data source name: RDS_Public_Database
- Instance ID: select your database from the drop-down
- Connection type: Public network
- Database name: QuickSightDatabase
- Username: admin (or the username you created when you set up your RDS instance)
- Password: enter in your RDS instance password
- Select Validate connection


  ![image](https://github.com/user-attachments/assets/f3dc1c57-6a88-4917-b423-7d1ce41180ba)



![image](https://github.com/user-attachments/assets/0ef5c7e8-098c-4ffb-b81d-8a79c01d5ba7)


# Secure QuickSight :

We can put QuickSight in a Security Group and our RDS in a Security Group, then let our RDS Security accept requests from the QuickSight security group only.
![image](https://github.com/user-attachments/assets/ba66e4dd-c618-44b1-98e9-d7610c9b5b55)

# Create security group for QuickSight
- Select Create security group
- For Security group name enter QuickSight_SecGp
- For Description enter Security Group that contains QuickSight
- Select the default VPC as your VPC option. We haven't created our own VPC so the default one is what our RDS and 
  QuickSight will be living in.

![image](https://github.com/user-attachments/assets/39c0166c-4cbc-4c16-9542-1ebdf51a82c1)

- Leave the inbound and outbound rules as they are.
- Select Create security group
- Take note of your new QuickSight_SecGp ID; take a screenshot or copy and paste it somewhere safe. You'll need it 
  so we can attach our new security group to QuickSight!
![image](https://github.com/user-attachments/assets/a8552121-89e8-4772-8aac-000113ef9fa3)
  NOW , We have an empty QuickSight Security Group living inside the same VPC as our RDS instance.

![image](https://github.com/user-attachments/assets/00ce99d3-8fd8-4aad-90eb-92e42953c46c)

# Attach Security Group to QuickSight
- Navigate to QuickSight using the search bar.
- Select the profile icon in the top right and select Manage QuickSight from the dropdown.
- Select Manage VPC connections
- Select the Add VPC connection button
- For VPC connection name, enter RDS_VPC
- Select the VPC from the dropdown that matches the one you added to your QuickSight security group. If you only see 
  one VPC in the dropdown, that'll be it!
- For Execution role, select aws-quicksight-service-role-v0.
- Select the default dropdown options for the Subnet ID fields
- For Security Group IDs select the same ID as your QuickSight_SecGp which you saved earlier.
![image](https://github.com/user-attachments/assets/d620ed14-ceb2-48f8-b533-91302cf14009)
![image](https://github.com/user-attachments/assets/63b2fa1c-845f-4815-9d6b-615397dbaead)
 # this ERROR WILL OCCUR BCOZ OUR ROLE ASSIGNED HAS NO VPC PERMISSIONS
 ![image](https://github.com/user-attachments/assets/90f65e8c-3b93-47ac-af1a-5f61d239de48)
# NAVIGATE TO IAM AND CHANGE ROLE AND ADD VPC ACCESS POLICY:
![image](https://github.com/user-attachments/assets/176030f1-bc2d-4668-8e5f-a6b75fad53fc)

- Click into the aws-quicksight-service-role-v0
- In the Permissions policies section, select Add permissions
- From the dropdown, select Create inline policy
- Select the JSON option as a policy editor
- Paste in the following IAM policy:

      {
       "Version": "2012-10-17",
       "Statement": [
       {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeVpcs",
        "ec2:DescribeSubnets",
        "ec2:DescribeSecurityGroups",
        "ec2:DescribeNetworkInterfaces",
        "ec2:CreateNetworkInterface",
        "ec2:DeleteNetworkInterface",
        "ec2:ModifyNetworkInterfaceAttribute",
        "iam:PassRole"
      ],
      "Resource": "*"
      },
      {
      "Effect": "Allow",
      "Action": [
        "iam:PassRole"
      ],
      "Resource": "*"
        }
       ]
      }

- Select Next
- For Policy name, enter QuickSightAllowVPC
- Select Create policy
![image](https://github.com/user-attachments/assets/a98034f4-96d0-49ae-8dda-0dc27981b0a3)

- Return to your QuickSight VPC connection.
- Select Add one more time.

  ![image](https://github.com/user-attachments/assets/8c7e23e4-fd9c-4c59-a053-213da99a83ca)

# Secure RDS 

- Make our RDS instance private instead of publicly accessible.
- Create a new security group specially for our RDS instance.
- Give our QuickSight security group access to our RDS securtiy group so they can talk to each other.

****Make your Database Not Publicly Accessible

- The database no longer needs to be publicly accessible; that's way too sketchy. We're going to do a much better 
   job with security groups.
- Open the Amazon RDS console, in the left-hand navigation, select Databases.
- Then, choose QuickSightDatabase
- On the QuickSightDatabase page, choose Modify.
- On the ModifyDB instance: QuickSightDatabase page, in the Connectivity section, choose Additional Configuration.
- Select Not publicly accessible, and choose Continue.
- Select Apply immediately.
- Select Modify DB instance.
![image](https://github.com/user-attachments/assets/e6907155-002e-4215-85a6-95530cd8e24f)

****Create a security group for RDS

- Search for security groups in the search bar in your AWS console
- Select Create security group
- For Security group name enter RDS_SecGp
- For Description enter Security Group that contains RDS
- Select the default VPC as your VPC option. Our RDS security group will live in the same VPC as our QuickSight 
   security group.
![image](https://github.com/user-attachments/assets/30d66f68-84e5-481e-8e16-e7d3b250bb82)

****Add inbound rules to allow QuickSight to query our RDS instance;

- Under Inbound rules, select Add rule
- For Type select MYSQL/Aurora
- For Source select Custom and then search for the security group ID of your QuickSight_SecGp
![image](https://github.com/user-attachments/assets/37bb84c3-21d2-40f5-ac5a-f02c8e49ecc2)


# Now let's attach it to our RDS instance.
- Return to your RDS instance and select Modify
- Under the Connectivity section, look for Security group
- Select your newly created RDS_SecGp and remove any existing one.
![image](https://github.com/user-attachments/assets/a6748b20-f3a5-4abc-aa52-a456606fbd8b)
- Select Continue
- Select Apply immediately
- Select Modify DB instance
We've created our own RDS security group, added inbound rules to allow QuickSight in, and attached it to our RDS instance.
![image](https://github.com/user-attachments/assets/a83be472-0efa-4af3-99a6-0062e5edb0b2)

# Reconnect RDS with QuickSight
- Create a dataset in QuickSight to connect with our new security group
- Choose the table we want to query to create our charts
- Return to the QuickSight console (you may need to click the QuickSight logo in the top left to leave the 
  QuickSight VPC settings).
  ![image](https://github.com/user-attachments/assets/52f9fd47-f145-4faa-b204-e4905e2f7204)

- Select Datasets
- Select New dataset
- Select RDS
- Fill out the following values:
- Data source name: RDS_VPC_Database
- Instance ID: select your database from the drop-down
- Connection type: RDS_VPC (not 'Public network' - yay!)
- Database name: QuickSightDatabase
- Username: admin (or the username you created when you set up your RDS instance)
- Password: enter in your RDS instance password
- Select Validate connection

![image](https://github.com/user-attachments/assets/b17e00fb-e237-4a95-8dba-e995649ed30e)

- Select Create data source
- Select newhire as the table to visualize.
- Click Select
- Select Directly query your data and then Visualize.
![image](https://github.com/user-attachments/assets/b23f0471-412c-420e-a231-e97cb61c933b)

# Make some charts 
- Cancel any pop-up that shows and select the Vertical Bar Chart from the left hand Visuals section.
- Drag jobs into the x-axis.
- Drag salary into the Value measure.

![image](https://github.com/user-attachments/assets/51096544-bac5-400e-80c9-e47ebf930735)

- Continue adding any other charts you feel like!
- When you're ready, select Publish in the top right
- Name your dashboard RDS New Hire Data
- Select Publish Dashboard

# DASHBOARD CREATED 
![image](https://github.com/user-attachments/assets/33c95b95-8b5c-41d9-b254-d902f18d2d3d)

# DELETE RESOURCES

