# AWSLambdaAMIBackup

Automated AMI Backups on AWS for EC2 instances

This script will search for all instances having a tag with "Backup" or "backup" on it. As soon as we have the instances list, we loop through each instance and create an AMI of it. Also, it will look for a "Retention" tag key which will be used as a retention policy number in days. If there is no tag with that name, it will use a 7 days default value for each AMI.
After creating the AMI it creates a "DeleteOn" tag on the AMI indicating when it will be deleted using the Retention value and another Lambda function called "AWSlambdaAMICleanup".
