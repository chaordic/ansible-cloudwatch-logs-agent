# ansible-cloudwatch-logs-agent

An Ansible role to install AWS Cloudwatch Logs agent on CentOS 7 & CentOS 6 in case you can not use Amazon Linux. 


## Prerequisites

This role assumes you run an AMI provide by CentOS on AWS.

## Usage

Include the folder in your roles directory. 

If you want to run this playbook locally you can do the following.

Clone the repository

```shell
git clone https://github.com/bitintheskud/ansible-role-cloudwatch-logs-agent.git
cat > playbook.yml
---
- name: Test cloudwatch role
  hosts: 127.0.0.1
  become: yes
  roles:
    - { role: '<YOUR PATH>/ansible-role-cloudwatch-logs-agent' }
```

Run ansible-playbook

```shell
ansible-playbook  -i "localhost," -c local playbook.yml
```

You need to attach a role to your instance to access AWS cloudwatch. 

see: https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/QuickStartEC2Instance.html

## Tricks 

Get the latest CentOS AMI id by running :

```
aws --region eu-west-1 ec2 describe-images \
    --owners aws-marketplace \
    --filters Name=product-code,Values=aw0evgkw8e5c1q413zgy5pjce \
    --query 'sort_by(Images, &CreationDate)[-1].[ImageId]' \
    --output 'text'
```

## License

MIT
