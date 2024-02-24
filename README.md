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


