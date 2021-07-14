# AWS-AUTOSCALING
Amazon EC2 Autoscaling helps us ensure that we have the correct number of Amazon EC2 instances available to handle the load for our application. We can create collections of EC2 instances, called Auto Scaling groups. We can specify the minimum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling ensures that our group never goes below this size. We can specify the maximum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling ensures that your group never goes above this size. If we specify the desired capacity, either when we create the group or at any time thereafter, Amazon EC2 Auto Scaling ensures that our group has this many instances. If we specify scaling policies, then Amazon EC2 Auto Scaling can launch or terminate instances as demand on our application increases or decreases.

Autoscaling mainly comprise of 4 important steps:
1. Launch an instance.

2. Create an image.

3. Launch Configurations

4. Autoscaling Groups
# Step 1: Launch an Instance
After logging in to AWS, select EC2 in the AWS services. To launch a new configuration, click on Launch Instances.


Choose an Amazon Machine Image(AMI). We will select Microsoft Windows Server 2016 Base to have Graphical Interface.

Instance type will be t2.micro. Click on Next.

In Configure Instance Details, we will launch only 1 instance and let Autoscaling group launch instances according to requirements. Click on Next: Add Storage.

Keeping Add Storage and Add Tags to default.

In Configure Security Group, We will create a new security group named autoscaledemo, keeping Description to default. Choose RDP for remote connection to Windows system and HTTP and HTTPS to allow internet traffic to reach our instances. Select Source to Anywhere for all the 3 types as shown below.

Final step to launch an instance is to choose a key-pair. Create a new key-pair and give it a name of your choice. Download key-pair and launch instances.

After 1-2 minutes your instances will be in running state. Give name to the launched instance to avoid any confusion.



# Step 2:Creating Image
Select the running instance and Click on Actions present Left of Launch Instances and further select Images and Templates and Create Image.

Enter any name of your choice in Image name. I will choose autoscaledemo. Keeping all other settings to default, Click on create instance image.

AMI image is successfully created.


# Step 3:Creating Launch Configuration
In the left navigation Panel, under Autoscaling select Launch Configurations. Click on Create Launch Configuration.

Give a Launch Configuration name and Choose AMI name of the one we created in Step 2. I will select autoscaledemo.

Select Instance type as t2.micro. Keeping Additional Configuration and Storage to default, we will choose existing security group, the one we created while launching our instance.

Use existing key-pair, same as one created while launching an instance. Click on Launch Configurations.

# Step 5:Creating Auto Scaling Group
Enter group name and Switch to launch configurations and select the configuration name we created in Step 3. Click on Next.

Choose VPC as default and select all the available subnets to balance the load. Click on Next.

We are not using Load Balancers. In Health Check, Health Check type by default will be EC2 because we have launched an instance and will select Health Check grace period as 120 seconds. Health Check Grace period is the amount of time until the EC2 Auto scale performs the first health check on new instances after they are put into services. Click on Next.

We will keep Desired Capacity 2 as we want Autoscaling group to make 2 instances available to us. Minimum Capacity as 1, available instances should never be less than this size and Maximum Capacity as 5, number of instances should never exceed this size.

Selecting Target Tracking Scaling Policy and using Average CPU utilization as Metric Size and setting Target Value as 50, an instance will be launched if CPU utilization exceeds Target Value. Instances need 120 seconds warm up before including in Metric. Click on Next.

Keeping other settings by default. Click on Create Autoscaling Group.
Autoscaling group is created. We will see 2 new instances being launched. If we increase load on server, more instances will be launched according to need.


# Connecting to original instance using RDP.
Select the instance and click on Connect.

In RDP client, click Get Password.

Browse the key-pair you used while launching the instance and click on Decrypt Password.

Download the Remote Desktop file and copy the password.

Open Remote Desktop file and proceed. Enter the copied password when asked for. Windows Server is connected to our system.

To increase CPU utilization, create a .bat file and open the file multiple times. When CPU utilization increase to a limit, new instances will be launched.





