apt-get update -y && apt-get install awscli -y

aws help

aws [options] <command> <subcommand> [parameters]
  
aws configure

    root@ip-172-31-44-54:~# aws configure
    AWS Access Key ID [None]: AKIA*******PQ
    AWS Secret Access Key [None]: hrl****************Gq1OHjR1
    Default region name [None]: us-east-1
    Default output format [None]: json

1. EC2: https://docs.aws.amazon.com/cli/latest/reference/ec2/index.html

        aws ec2 describe-instances

        aws ec2 describe-instances --output table

        aws ec2 describe-volumes --output text
        
        aws ec2 run-instances help
        
        aws ec2 run-instances --image-id ami-026b6eb3e6c3027e8 --count 1 --instance-type t2.micro --key-name aws-2
        
        aws ec2 run-instances --image-id ami-026b6eb3e6c3027e8 --count 1 --instance-type t2.micro --key-name aws-2 --security-group-ids sg-068402cee3c9b7f81
        
        aws ec2 create-tags --resources i-07f5dc2f7b4a019f0 --tags Key=Name,Value=MyInstance
              
        aws ec2 describe-instances --filters "Name=tag:Name,Values=MyInstance"
        
        aws ec2 describe-instances --filters "Name=tag:Name,Values=MyInstance" --output table
        
        aws ec2 describe-instances --filters "Name=instance-type,Values=t2.micro"
        
        aws ec2 terminate-instances --instance-ids i-07f5dc2f7b4a019f0 --output table

![image](https://user-images.githubusercontent.com/24622526/49352204-d618fd00-f6dc-11e8-9eab-3756290d7dbc.png)


        aws ec2 create-key-pair --key-name aws-3 --query 'KeyMaterial' --output text > aws-3.pem
        
        cat aws-3.pem
        
        aws ec2 run-instances --image-id ami-026b6eb3e6c3027e8 --count 1 --instance-type t2.micro --key-name aws-3
        
        chmod 400 aws-3.pem
        
        ssh -i "aws-3.pem" ubuntu@ec2-34-207-96-190.compute-1.amazonaws.com
        
        exit
        
        aws ec2 describe-key-pairs --key-name aws-2
        
        aws ec2 describe-key-pairs --key-name aws-3
        
        aws ec2 delete-key-pair --key-name aws-3
        
        aws ec2 create-security-group --group-name mySg --description "My security group"
        
        aws ec2 create-security-group --group-name mySg --description "My security group" --vpc-id vpc-1a2b3c4d
        
        aws ec2 describe-security-groups
        
        aws ec2 describe-security-groups --group-ids sg-0f6d2f1f102155f13
        
        aws ec2 authorize-security-group-ingress --group-id sg-0f6d2f1f102155f13 --protocol tcp --port 3389 --cidr 203.0.113.0/24
        
        aws ec2 authorize-security-group-ingress --group-id sg-0f6d2f1f102155f13 --protocol tcp --port 22 --cidr 0.0.0.0/0
        
2. AMI

        
        
2. Create LB

3. Create LC, ASG

4. Attach LB to ASG.

5. Create VPC

6. Create S3.

