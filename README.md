# AWS-Visualize-a-Relational-Database
The goal of this project is to set up our own relational database and visualize it using some charts all using AWS.

![image](https://github.com/user-attachments/assets/bfe10f71-6816-4d12-89cb-8e6fa4257b51)

# Login with your IAM user

![image](https://github.com/user-attachments/assets/182d0326-164a-4f23-8a24-f8e628a1221d)

# Create a Relational Database

Head to your RDS console - search for rds in search bar at the top of the screen.


![image](https://github.com/user-attachments/assets/c2ccd75e-c792-415d-95b0-c3a71af45f9b)

In the left navigation bar, select Databases.
In the Database section, select Create Database.
On the Create database page, choose Easy Create.
In the Configuration section, make the following changes:
For Engine type, choose MySQL.
For DB instance size, choose Free tier.

![image](https://github.com/user-attachments/assets/fbeb6a6b-f580-46d1-9b9b-5189bd423b57)

For DB instance identifier, type QuickSightDatabase.
For Master username, enter admin.
In the Credentials management section, select Self managed
For Master password, type a unique password, and confirm password.
Make sure you save your database login details somewhere safe! You'll need them later on.

![image](https://github.com/user-attachments/assets/bac7dad3-e78b-464b-a46e-77c6d13a37b5)

Leave the rest as the default settings and select choose Create database.

# This is what we created in this step:
![image](https://github.com/user-attachments/assets/dfd9cdc0-8916-4d0e-837a-885e15cb9362)
