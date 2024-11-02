# Serverless EC2 Instance Scheduler for Company Working Hours 
## Scenario :
In some companies there is no need to run EC2 instances 24/7; You need instances for a specific time, such as company working hours, from 8:00 AM in the morning to 5:00 PM in the evening. To handle this scenario, I use two Lambda functions that are responsible for starting and stopping instances. This Lambda function will be triggered by CloudWatch Events both in the morning and in the evening. This solution is completely serverless.

![Architecture](https://github.com/itz-mathesh/serverless-ec2-scheduler/assets/144098846/287063a4-964a-4f8b-b88e-25535b7f4691)


## Setup Guide  :

### Step 1 :
### Creating the Instance :
1. Go to the EC2 Console.
2. Follow the steps below.

### Step 2 :
### Creating the Policy :

1. Navigate to the IAM Console.
2. Click on "Policies" and then Click on "Create policy"
