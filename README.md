# Serverless EC2 Instance Scheduler for Company Working Hours 
## Scenario :
In some companies there is no need to run EC2 instances 24/7; You need instances for a specific time, such as company working hours, from 8:00 AM in the morning to 6:00 PM in the evening. To handle this scenario, I use two Lambda functions that are responsible for starting and stopping instances. This Lambda function will be triggered by CloudWatch Events both in the morning and in the evening. This solution is completely serverless.

![Architecture](screenshot/1.png)


## Setup Guide  :

### Step 1 :
### Creating the Instance :
1. Go to the EC2 Console.
2. Follow the steps below.

![1](screenshot/2.png)
![1](screenshot/3.png)
![1](screenshot/4.png)
![1](screenshot/5.png)

### Step 2 :
### Creating the Policy :

1. Go to the IAM Console.
2. Click on "Policies" and then Click on "Create policy"

![2](screenshot/6.png)


3. Select services as EC2.
4. And Actions are DescribeInstances , StartInstances.

![2](screenshot/6.png)

![2](screenshot/7.png)

![2](screenshot/8.png)

![2](screenshot/9.png)

![2](screenshot/10.png)

![2](screenshot/11.png)



6. Now we have created a policy for starting instances. We also need to create a policy for stopping the instances. This is because we are going to create two Lambda functions: one for starting and one for stopping the instances. Each function will have its own role, and we will attach these two policies to their respective roles.<br>
7. Now  we are going to repeat the same steps for Creating Stopping Policy also.<br>
8. Everything is same , Except Actions because we are going to stop the instance.<br>
9. The Actions are DescribeInstances , StopInstances .<br>
10. Keep your Plolicy name as "stop-ec2-instance".

## Step 3 :
## Creating the Lambda functions :

1. Go to the lambda Console.
2. Follow the Outlined steps below.

![3](screenshot/12.png)

![3](screenshot/13.png)

![3](screenshot/14.png)

![3](screenshot/15.png)

![3](screenshot/16.png)

![3](screenshot/17.png)

Now again , go to the Lambda console and then test the code.

![2](screenshot/18.png)

![2](screenshot/19.png)

3. Now we Created  alambda function for Starting Instance.
4. We have to Reapeat the same steps again to Create a Lambda function for Stopping Instance , Keep your lambda function name as "Stop-EC2-demo".
5. The only changes we have to make are to replace the default code with the 'stop-ec2-instance.py' code and attach the policy we created for stopping instances to the role of this Lambda function.

 [2](screenshot/20.png)

6. As demonstrated above, when I test my Python code, it runs successfully and stops the instance.
7. Now, we are ready to proceed and create schedules for this functions.

### Step 5 :
### Creating the Schedules Using Cloud Watch :

1. Go to the Cloud Watch Console.
2. Follow the Outlined Steps below.

 [2](screenshot/21.png)
 
 [2](screenshot/22.png)
 
 [2](screenshot/23.png)
 
 [2](screenshot/24.png)
 
 [2](screenshot/25.png)
 
 [2](screenshot/26.png)
 
 [2](screenshot/27.png)
 
 [2](screenshot/28.png)
 
 [2](screenshot/29.png)
 
 [2](screenshot/30.png)

 3. We have now created a schedule for starting the instance every day at 8:00 AM.<br>
4. Next, we need to create a schedule for stopping instances.<br>
5. To create the schedule for stopping instances, follow the same steps as for starting instance scheduling with a few changes, Keep your rule name as "stop-ec2-rule".<br>
6. The changes include modifying the scheduled time and selecting the appropriate scheduling function.<br>
7. We need to change the schedule time to 18:00 because it will stop the Lambda function at 18:00 IST (6:00 PM).

 [2](screenshot/31.png)

 8. We have to Change the Function as Stop-EC2-demo

 [2](screenshot/32.png)

9. Now, we have successfully created two schedules: one to start the instance every day at 8:00 AM and the other to stop the instance every day at 6:00 PM.


 [2](screenshot/33.png)


