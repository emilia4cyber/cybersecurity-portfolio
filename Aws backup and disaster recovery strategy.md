# AWS Backup and Disaster Recovery Strategy

## About the project
This project provides  an example of a well-defined AWS Backup plan , including IAM role configuration, cross-region backups, automated alerts, and disaster recovery planning. 

## Step 1: Creating IAM Roles
I created an IAM role named `Backup-Role` in the IAM console and attached the following policies:

- **AWSBackupServiceRolePolicyForBackup** – 1for being able to create, configure and manage backups.
- **AmazonRDSFullAccess** – for getting access to RDS backups.
- **AmazonDynamoDBFullAccess** – for getting access to DynamoDB backups.
- **AmazonElasticFileSystemFullAccess** – for getting access to EFS backups.
- **IAMReadOnlyAccess** – to allow for auditing. (Check [screenshot](https://ibb.co/jvFv4sCv))

## Step 2: Creating a New Policy for Cross-Region Backup
- I created a new policy: **AWSBackupServiceRolePolicyForCrossRegionBackup** to facilitate cross-region backups. (Check [screenshot](https://ibb.co/bjX9XG6r))

## Step 3: Attaching the Cross-Region Backup Policy
- Created a new IAM role: **AWSBackupCrossRegionRole**  (Check [screenshot](https://ibb.co/zzW84zY)) and attached the following policies:
  - AWSBackupServiceRolePolicyForBackup
  - AWSBackupServiceRolePolicyForRestores
  - AWSBackupServiceRolePolicyForCrossRegionBackup (Check [screenshot](https://ibb.co/1SjQ3jD))

## Step 4: Setting up Backup Plans and Vaults
I created backup plans for critical AWS services and configured vaults as follow:

- **RDS Backup Plan** → Stored in `RDS-Backup-Vault` (destination region)
- **DynamoDB Backup Plan** → Stored in `Dynamo-Backup-Vault` (destination region)
- **EFS Backup Plan** → Stored in `EFS-Backup-Vault` (destination region)

### Cross-Region Backup
- Primary region: **Asia Pacific (Mumbai)**
- Destination vaults for cross-region backups:
  - `EFS-Backup-Vault`
  - `Dynamo-Backup-Vault`
  - `RDS-Backup-Vault`
 Screenshots with the process: [1](https://ibb.co/4wcjf6NR), [2](https://ibb.co/cSjWfmCy), [3](https://ibb.co/cc1RQhvq), [4](https://ibb.co/XfB5Vq4j).


## Step 5: Applying Backup Vault Lock for Data Protection
- I applied **Backup Vault Lock** for **4 years** on `Dynamo-Backup-Vault` to prevent accidental deletion. (check [screenshot](https://ibb.co/GQNf0M2v))

## Step 6: Simulating Backup Job Failure and Setting Up Automated Alerts
For proactive backup monitoring, I simulated a failure scenario and implemented automated alerts.

### Step 6.1: Configure Amazon SNS for Backup Alerts
- I accessed **SNS Console** and then I created a new topic: `BackupAlerts`.
- I created an **email subscription** to receive failure notifications. (check [screenshot](https://ibb.co/v4Yg1s1Q))
- I confirmed subscription via email.

### Step 6.2: Set up  AWS EventBridge to Capture Backup Failures
- I accessed **EventBridge Console** to create a new rule: `BackupStatusAlerts`. (check [screenshot](https://ibb.co/qYDDbdnP))
- Selected **SNS topic** (`BackupAlerts`) as target. (check [screenshot](https://ibb.co/k6cdqFvR))
- I simulated a **failed backup job**:
  - I created an on-demand backup for **DynamoDB Backup Plan**. 
  - Then I stopped the backup process to trigger the failure. (check [screenshot](https://ibb.co/Kc69G2kg))
- Received a **notification email** confirming the failure. (check [screenshot](https://ibb.co/C30Mx60t))

## Challenges
During this project, I gained valuable experience in configuring AWS Backup and integrating it with other services like SNS and EventBridge. 

Some of the challenges encountered included missing policies (which I had to create) and creating a table for enabling on-demand backup.

## Learnings

- I learned better how to master data protection and to prevent accidental deletion

- How to recover fast the services in case of regional outage or other distasters

- How to automate alerts or processes and to reduce manual effort.

