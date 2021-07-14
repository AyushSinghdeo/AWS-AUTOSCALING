# AWS-AUTOSCALING
Amazon EC2 Autoscaling helps us ensure that we have the correct number of Amazon EC2 instances available to handle the load for our application. We can create collections of EC2 instances, called Auto Scaling groups. We can specify the minimum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling ensures that our group never goes below this size. We can specify the maximum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling ensures that your group never goes above this size. If we specify the desired capacity, either when we create the group or at any time thereafter, Amazon EC2 Auto Scaling ensures that our group has this many instances. If we specify scaling policies, then Amazon EC2 Auto Scaling can launch or terminate instances as demand on our application increases or decreases.









![11](https://user-images.githubusercontent.com/73579847/125653836-c0aee3e4-8b52-445a-bc11-24cc5c13c9af.png)
![22](https://user-images.githubusercontent.com/73579847/125653801-177a81ff-9551-49aa-a73f-f3c4a6661c7a.png)


Autoscaling mainly comprise of 4 important steps:
1. Launch an instance.

2. Create an image.

3. Launch Configurations

4. Autoscaling Groups

# Step 1: Launch an Instance
After logging in to AWS, select EC2 in the AWS services. To launch a new configuration, click on Launch Instances.
![1](https://user-images.githubusercontent.com/73579847/125654304-071ac88e-8329-4cc9-824f-9848abb04785.png)

Choose an Amazon Machine Image(AMI). We will select Microsoft Windows Server 2016 Base to have Graphical Interface.
![2](https://user-images.githubusercontent.com/73579847/125653809-247649a1-c088-4462-939f-c3a51c83f18d.png)

Instance type will be t2.micro. Click on Next.
![3](https://user-images.githubusercontent.com/73579847/125653810-7b6ad08b-83ee-4e63-bd93-047afd56a510.png)

In Configure Instance Details, we will launch only 1 instance and let Autoscaling group launch instances according to requirements. Click on Next: Add Storage.
![4](https://user-images.githubusercontent.com/73579847/125653816-15632d1a-238c-4ff8-becc-0901c859a43c.png)

Keeping Add Storage and Add Tags to default.
![5](https://user-images.githubusercontent.com/73579847/125654307-ef47ce61-f1ac-48f3-bd99-c2b867ef945e.png)

In Configure Security Group, We will create a new security group named autoscaledemo, keeping Description to default. Choose RDP for remote connection to Windows system and HTTP and HTTPS to allow internet traffic to reach our instances. Select Source to Anywhere for all the 3 types as shown below.
![6](https://user-images.githubusercontent.com/73579847/125654309-bd9fe5c1-37c9-49bb-93c0-6331aab7f224.png)

Final step to launch an instance is to choose a key-pair. Create a new key-pair and give it a name of your choice. Download key-pair and launch instances.
![7](https://user-images.githubusercontent.com/73579847/125653825-9e3500ea-b515-4022-b427-82b8e6e5c244.png)

After 1-2 minutes your instances will be in running state. Give name to the launched instance to avoid any confusion.
![8](https://user-images.githubusercontent.com/73579847/125653829-633cadb1-f96d-42ec-b778-7f7fd20dde7e.png)


# Step 2:Creating Image
Select the running instance and Click on Actions present Left of Launch Instances and further select Images and Templates and Create Image.
![9](https://user-images.githubusercontent.com/73579847/125653833-16288dc7-f593-4bb7-95e4-abe2649721fa.png)


Enter any name of your choice in Image name. I will choose autoscaledemo. Keeping all other settings to default, Click on create instance image.
![10](https://user-images.githubusercontent.com/73579847/125653834-f2d982cb-b73e-478b-9cae-8354a18727b1.png)

AMI image is successfully created.
![11](https://user-images.githubusercontent.com/73579847/125653836-c0aee3e4-8b52-445a-bc11-24cc5c13c9af.png)

# Step 3:Creating Launch Configuration

In the left navigation Panel, under Autoscaling select Launch Configurations. Click on Create Launch Configuration.
![12](https://user-images.githubusercontent.com/73579847/125653839-7d4c2319-73b9-489b-8137-f9bd5d852ab4.png)

Give a Launch Configuration name and Choose AMI name of the one we created in Step 2. I will select autoscaledemo.
![13](https://user-images.githubusercontent.com/73579847/125653843-ba02bc57-0543-47ba-a2ff-9a77862685ea.png)

Select Instance type as t2.micro. Keeping Additional Configuration and Storage to default, we will choose existing security group, the one we created while launching our instance.
![14](https://user-images.githubusercontent.com/73579847/125653848-7a9f3cf0-c43b-442a-a82e-f2385a2c9d92.png)

Use existing key-pair, same as one created while launching an instance. Click on Launch Configurations.
![15](https://user-images.githubusercontent.com/73579847/125653852-0298c86a-2045-4d7f-96f7-6014d22d3b66.png)

# Step 5:Creating Auto Scaling Group
Enter group name and Switch to launch configurations and select the configuration name we created in Step 3. Click on Next.

![16](https://user-images.githubusercontent.com/73579847/125653854-41845e52-953c-4752-a52d-ecda3bc69cb9.png)

Choose VPC as default and select all the available subnets to balance the load. Click on Next.
![17](https://user-images.githubusercontent.com/73579847/125653857-00c3d373-d3d1-4186-a7e5-2318ccaccbfe.png)

We are not using Load Balancers. In Health Check, Health Check type by default will be EC2 because we have launched an instance and will select Health Check grace period as 120 seconds. Health Check Grace period is the amount of time until the EC2 Auto scale performs the first health check on new instances after they are put into services. Click on Next.
![18](https://user-images.githubusercontent.com/73579847/125653864-c0d61a28-4ecb-40ee-a532-c896d7cd3699.png)

We will keep Desired Capacity 2 as we want Autoscaling group to make 2 instances available to us. Minimum Capacity as 1, available instances should never be less than this size and Maximum Capacity as 5, number of instances should never exceed this size.
![19](https://user-images.githubusercontent.com/73579847/125653789-e17355ae-ad2d-4994-8120-6440a09eef32.png)

Selecting Target Tracking Scaling Policy and using Average CPU utilization as Metric Size and setting Target Value as 50, an instance will be launched if CPU utilization exceeds Target Value. Instances need 120 seconds warm up before including in Metric. Click on Next.
![20](https://user-images.githubusercontent.com/73579847/125653796-2735b1dd-5030-47cb-951b-e4edc369fe35.png)

Keeping other settings by default. Click on Create Autoscaling Group.
Autoscaling group is created. We will see 2 new instances being launched. If we increase load on server, more instances will be launched according to need.
![21](https://user-images.githubusercontent.com/73579847/125654300-78a16000-c4c0-410a-92e2-8994aca2dd6e.png)

# Connecting to original instance using RDP.
Select the instance and click on Connect.
![22](https://user-images.githubusercontent.com/73579847/125653687-f6fa84f1-ef7c-4064-accc-258d4871ae97.png)

In RDP client, click Get Password.
![23](https://user-images.githubusercontent.com/73579847/125653678-a40d7ee2-e194-46eb-899e-ca80d85b9fb8.png)

Browse the key-pair you used while launching the instance and click on Decrypt Password.

Download the Remote Desktop file and copy the password.
![25](https://user-images.githubusercontent.com/73579847/125653674-b33f11d5-2630-4e9c-81a8-591e1ad2c648.png)

Open Remote Desktop file and proceed. Enter the copied password when asked for. Windows Server is connected to our system.
![26](https://user-images.githubusercontent.com/73579847/125653664-23e10a6f-6340-4bba-957f-6041a03bdd77.png)

To increase CPU utilization, create a .bat file and open the file multiple times. When CPU utilization increase to a limit, new instances will be launched.
![27](https://user-images.githubusercontent.com/73579847/125653629-b36a5103-2b67-4ba6-b7ec-cca640ca8a05.png)




