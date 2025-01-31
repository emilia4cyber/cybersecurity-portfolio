# Exercise 1: Choosing the Right Identity Source

##  Steps I followed:
1. Logged into AWS IAM Identity Center.
2. Navigated to Settings, then Identity Source.
3. Selected Identity Center Directory (the other 2 options available being Active Directory and External identity providers).

##  Proof of Work:
Screenshot: https://ibb.co/tPk3H2Lm


# Exercise 2: Creating a User

##  Steps I followed:
1. Accessed AWS IAM Identity Center left panel.
2. Selected "Users" and then "Add".
3. Created the user "test_user2025".
4. Made sure the account is activated and I could login without any issues.

 ##  Proof of Work:
Screenshots: https://ibb.co/4nYTwVcw and https://ibb.co/C3hDsxPB


# Exercise 3: Creating a Group and Adding a User

##  Steps I followed:
1. Accessed the AWS IAM Identity Center left panel.
2. Selected "Groups" and then "Add".
3. Created the group "party people".
4. Added the newly created user in the group.

##  Proof of Work:
Screenshot: https://ibb.co/ZRcc7Gcv 


# Exercise 4: Creating a Permission Set and Applying the Permission Set to the AWS Account

## Steps I followed:
1. Accessed the AWS IAM Identity Center left panel.
2. Clicked on Permission sets under the AWS Accounts section.
3. Chose the option Create permission set.
4. Selected AdministratorAccess (for full admin access).
5. Added the configuration to the user emilia.mat (the root admin) from the AWS accounts section
6. Selected test_user2025 and assigned the previously created AdministratorAccess permission set to the user.
7. Clicked Assign** to apply the permission.

##  Proof of Work:
Screenshots: https://ibb.co/BSMYb69 and https://ibb.co/RkFhKbsy
   





