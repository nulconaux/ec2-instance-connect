[![IaC](https://app.soluble.cloud/api/v1/public/badges/900d1b3f-d0b7-4d33-baed-6112d472f5ed.svg)](https://app.soluble.cloud/repos/details/github.com/nulconaux/d004-ec2-instance-connect-demo)  [![HIPAA](https://app.soluble.cloud/api/v1/public/badges/4d24c538-5c48-4a36-b65c-45e10668964e.svg)](https://app.soluble.cloud/repos/details/github.com/nulconaux/d004-ec2-instance-connect-demo)


# EC 2 Instance Connect

![image info](./images/1.png)


## Platforms:
    Amazon Linux 2 (any version)
    Ubuntu 16.04 or later

## Tasks to set up Instance Connect
```
Task 1: Configure network access to an instance
Task 2: (Conditional) Install EC2 Instance Connect on an instance
Task 3: (Optional) Install the EC2 Instance Connect CLI
Task 4: Configure IAM permissions for EC2 Instance Connect
```

## Client configuration
```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION="eu-west-2"
```

`pip install ec2instanceconnectcli`

Bugs: 
```
An HTTP Client raised an unhandled exception: Failed to parse: https://ec2.eu-west-2.amazonaws.com/
```

@ `pip3 install six==1.15.0 launchpadlib`


## Create demo env

```
packer build packer.json
cd terraform/examples/ec2-eu-west-2/
terraform apply --auto-approve
```


    
## Manually installation (alredy in packer)


```
sudo yum install ec2-instance-connect
AuthorizedKeysCommand /opt/aws/bin/eic_run_authorized_keys %u %f
AuthorizedKeysCommandUser ec2-instance-connect
```

## Policies
```
aws iam create-policy --policy-name my-policy --policy-document file://policies/*.json
aws iam attach-user-policy --policy-arn arn:aws:iam::account-id:policy/my-policy --user-name IAM-friendly-name
```


# Usage

## Option 1: GUI
![gui](./images/4.png)

## Option 2: Push keys
![push](./images/2.png)

## 3. Option 3: mssh
![mssh](./images/3.png)





```
mssh usage:
                 mssh [-t instance_id] [-u profile] [-z availability_zone] [-r region] [supported ssh flags] target [command]
     
                 target                => [user@]instance_id | [user@]hostname
                 [supported ssh flags] => [-l login_name] [-p port]

msftp usage:
            msftp [-u aws_profile] [-z availability_zone] [supported sftp flags] target
            target                 => [user@]instance_id[:file ...][:dir[/]] | [user@]hostname[:file ...][:dir[/]]
            [supported sftp flags] => [-P port] [-b batchfile]
```


### ip-ranges

https://ip-ranges.amazonaws.com/ip-ranges.json

`jq -r '.prefixes[] | select(.region=="eu-west-2") | select(.service=="EC2_INSTANCE_CONNECT") | .ip_prefix' < ip-ranges.json`

allow HTTPS inbound 3.8.37.24/29

