# prometheus on ecs

## How to build on local

```bash
docker-compose -file docker-compose.dev.yml up
```

## How to build on ECS

```bash
# Setting Cluster
ecs-cli configure --cluster ec2-tutorial --region us-east-1 --default-launch-type EC2 --config-name ec2-tutorial

# Setting ecs-cli configure
ecs-cli configure profile --access-key AWS_ACCESS_KEY_ID --secret-key AWS_SECRET_ACCESS_KEY --profile-name tutorial-profile

# Deploy on Cluster
ecs-cli compose up --create-log-groups --cluster-config ec2-tutorial --ecs-profile tutorial-profile

# Create Cluster
ecs-cli up --keypair vimana --capability-iam --size 2 --instance-type t2.medium --cluster-config ec2-tutorial --ecs-profile tutorial-profile --force

# Service ins
ecs-cli compose service up --cluster-config ec2-tutorial --ecs-profile tutorial-profile
```