# AWS RDS Terraform module
![squareops_avatar]

[squareops_avatar]: https://squareops.com/wp-content/uploads/2022/12/squareops-logo.png

### [SquareOps Technologies](https://squareops.com/) Provide end to end solution for all your DevOps needs
<br>
The terraform-aws-rds-mysql module is a reusable infrastructure-as-code solution for deploying and managing an Amazon RDS MySQL database cluster using Terraform. It simplifies the process of provisioning and configuring a highly available and scalable MySQL database environment in AWS.
Features

  1. High Availability: The module sets up a multi-AZ (Availability Zone) database cluster for enhanced fault tolerance and automatic failover.
  2. Scalability: Easily scale your database cluster by adjusting the instance count and instance type according to your needs.
  3. Security: The module integrates with AWS Identity and Access Management (IAM) for secure authentication and fine-grained access control.
  4. Backup and Recovery: Automated backups can be scheduled, and the module provides options for specifying the retention period and whether to skip a final snapshot during deletion.
  5. Encryption: Database encryption at rest can be enabled to ensure data security.
  6. Maintenance Window: Configure a maintenance window for performing regular database maintenance tasks.
  7. Public Accessibility: Choose whether the database cluster should be publicly accessible over the internet.
  8. Replication: Replicate data from another Amazon RDS database by specifying the source database identifier.
  9. Snapshot Restore: Restore the database from a specified snapshot ID to easily recreate database instances.
  10. VPC Support: Deploy the RDS cluster in a specific Virtual Private Cloud (VPC) and specify the associated subnets for network isolation.
  11. CloudWatch Alerts: Set up CloudWatch alarms to monitor the health and performance of your Redis cluster. Integrate these alarms with AWS Simple Notification Service (SNS) to receive real-time alerts. Use AWS Lambda functions to customize your alerting logic, and send notifications to Slack channels for immediate visibility into your RDS MYSQL status.
  12. Supports feature for storage autoscaling to avoid the storage bottleneck and Replica configuration with desired number of replicas.

## Usage Example

```hcl
module "rds-mysql" {
  source  = "squareops/rds-mysql/aws"

  name                             = "name"
  vpc_id                           = "vpc-0d2c255df1f"
  replica_enable                   = false
  replica_count                    = 1
  subnet_ids                       = ["subnet-04cecf2400","subnet-0ac69f821"]
  family                           = "mysql8.0
  db_name                          = "proddb"
  availability_zone                = "us-east-2a"
  multi_az                         = false
  environment                      = "prod"
  kms_key_arn                      = "arn:aws:kms:us-east-2:2222222222:key/a22ecc12-4-ae1be7590774"
  engine_version                   ="8.0.32"
  instance_class                   = "db.t3.medium"
  master_username                  = "admin"
  allocated_storage                = 20
  rds_instance_name                = "mysql"
  major_engine_version             = "8.0"
  allowed_security_groups          = ["sg-0e2f946c67"]
  publicly_accessible              = false
  skip_final_snapshot              = true
  backup_window                    = "03:00-06:00"
  snapshot_identifier              = null
  maintenance_window               = "Mon:00:00-Mon:03:00"
  final_snapshot_identifier_prefix = "prod-snapshot"
  deletion_protection              = true
  cloudwatch_metric_alarms_enabled = true
  alarm_cpu_threshold_percent      = 70
  disk_free_storage_space          = "10000000" # in bytes
  slack_username                   = "John"
  slack_channel                    = "skaf"
  slack_webhook_url                = "https://hooks/xxxxxxxx"
  custom_user_password             = "mysqlpassword"
}

```


