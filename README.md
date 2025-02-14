# AWS Backup Strategy Project Overview

With this project I wanted to create a  Backup plan, in which to include IAM role configuration, cross-region backups, automated alerts, and disaster recovery.

## Steps I followed:

### 1. IAM Role Configuration
- Created `Backup-Role` and attached policies:
  - `AWSBackupServiceRolePolicyForBackup`
  - `AmazonRDSFullAccess`, `AmazonDynamoDBFullAccess`, `AmazonElasticFileSystemFullAccess`
  - `IAMReadOnlyAccess`

### 2. Cross-Region Backup Setup
- Created `AWSBackupServiceRolePolicyForCrossRegionBackup`
- Assigned it to `AWSBackupCrossRegionRole` with further backup policies

### 3. Backup Plans & Vaults
- Configured backup plans for RDS, DynamoDB, and EFS
- Stored backups in dedicated vaults with cross-region replication to Asia Pacific (Mumbai)

### 4. Backup Vault Lock
- Applied a 4-year lock on `Dynamo-Backup-Vault` to prevent accidental deletion

### 5. Automated Backup Alerts
- **SNS:** Created `BackupAlerts` topic and email subscription
- **EventBridge:** Created `BackupStatusAlerts` rule linked to SNS
- Tested by simulating a backup failure and confirmed email alerts

Hope you find my work interesting! :)
