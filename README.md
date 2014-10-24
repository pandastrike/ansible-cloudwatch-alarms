ansible-cloudwatch-metrics
==========================

This script uses Ansible's ec2_metric_alarm module to create/update alarms based on CPU, disk space, memory, and swap utilization.  

It requires AWS keys and, if you want the alarms to actually be useful, the target instance to be consistently sending its metrics.  
The previous, accompanying Ansible role to send metrics can be found here: https://github.com/pandastrike/ansible-cloudwatch-metrics  

Required variables:  
`aws_credential_file_dest`: location of AWS credential file on target instance  
`alarm_recipients`: array of alarm actions  
`alarm_region`: one of the AWS regions (http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)  

Optional variables:  
`tag_project`: project name or meta data, used for alarm name classification  
`env`: environment (e.g. "production", "staging", etc)  

Example group_vars/all file:  
```
aws_credential_file_dest: "{{cloudwatch_dir}}/aws-scripts-mon/awscreds.template"
alarm_recipients: ["arn:aws:sns:us-west-1:1234567890:Peter"]
```

Example optional variables:  
```
tag_project: glideroom
env: production
```

