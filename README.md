# AWS EC2 Auto Scaling Project

This project demonstrates setting up EC2 Auto Scaling with CloudWatch Alarms and a Lambda function to handle scaling actions.

## Steps

### Step 1: Configure EC2 Auto Scaling Group (ASG)
1. **Go to the EC2 Console**.
2. **Create a Launch Template**:
   - Provide details like **AMI** and **Instance Type**.
   - Add **Security Groups** and configure **Key Pairs** for SSH access.
3. **Create Auto Scaling Group**:
   - In the **Auto Scaling Groups** section, select your launch template.
   - Configure **VPC and subnets**.
   - Set **Desired Capacity**, **Minimum Capacity**, and **Maximum Capacity** values.

### Step 2: Setup CloudWatch Alarms
1. **Go to the CloudWatch Console**.
2. **Create High CPU Usage Alarm**:
   - Set the alarm to trigger when **CPUUtilization > 75%**.
   - Set actions to send notifications to an SNS topic.
3. **Create Low CPU Usage Alarm**:
   - Set the alarm to trigger when **CPUUtilization < 25%**.
   - Send notifications to the same SNS topic.

### Step 3: Configure SNS and EventBridge
1. **Create an SNS Topic** for notifications.
2. **Update CloudWatch Alarms** to publish to the SNS topic created.
3. **Configure EventBridge**:
   - Create a rule to listen for SNS events.
   - Add your **Lambda function** as the target to handle scaling actions.

### Step 4: Write and Deploy Lambda Function
1. **Go to the Lambda Console**.
2. **Create a Lambda function**:
   - Choose an IAM role with permissions for EC2 and Auto Scaling.
   - Write the code to manage scaling based on incoming SNS events.

### Step 5: Test and Validate
1. **Create Load on EC2 Instances** to trigger alarms.
2. **Check CloudWatch and Lambda Logs** to confirm scaling actions.
3. **Verify in the EC2 Console** that instances are scaling as expected.

---

## Clean Up Resources
- Terminate EC2 instances.
- Delete the Auto Scaling group, Lambda function, CloudWatch alarms, and EventBridge rule to avoid unnecessary costs.

---


