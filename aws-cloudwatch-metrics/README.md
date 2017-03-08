# AWS Cloudwatch metrics role

This role installs and configures __AWS's__ provided Cloudwatch __perl__ scripts for on Host (EC2) metrics.


## Requirements

You'll need minimum __IAM__ permissions to be able to put metrics to cloudwatch from your instances.

Here is an policy example that you can associate to an instance profile:

```json
{
  "Statement": [
    {
      "Action": [
        "cloudwatch:PutMetricData",
        "ec2:DescribeTags"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}
```

## Usage example

Clone directory:

```bash
git clone https://github.com/d2si-oss/ansible-roles
cd ansible-roles/
```

`monitoring.yml`, sample playbook file:

```yaml
---
- hosts: all
  become: yes
  gather_facts: no
  remote_user: admin
  roles:
  - cloudwatch-metrics
...
```

`inventory`, target host inventory:

```
host1
host2
```

Run playbook:

```bash
ansible-playbook -i inventory monitoring.yml
```

## Disclaimer

This role is currently up and tested on __Debian__ and __Ubuntu__.
Other Linux family will be provided soon.
