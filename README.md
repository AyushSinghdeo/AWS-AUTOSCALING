# AWS-AUTOSCALING
Aws autoscaling step by step
# Step 1:
First go to EC2 Dashboard and create EC2 instance

![repo1](https://user-images.githubusercontent.com/73579847/123121561-e2176680-d462-11eb-91b4-c3fb57634fb2.jpg)

# Step 2:
Then create image
Select instace -> go to action -> select images and templet -> select create image

![repo2](https://user-images.githubusercontent.com/73579847/123122772-ebed9980-d463-11eb-9de7-8a3714c51922.jpg)

![repo3](https://user-images.githubusercontent.com/73579847/123123074-2eaf7180-d464-11eb-80f8-1bb19b311e91.jpg)

# Step 3:
Then create lunch configuration
![repo4](https://user-images.githubusercontent.com/73579847/123124183-155af500-d465-11eb-90f8-79ef770c1c75.jpg)

![repo5](https://user-images.githubusercontent.com/73579847/123124208-1b50d600-d465-11eb-89bc-04002fd5b344.jpg)

# Step 5:
Then create Autoscaling group
![repo6](https://user-images.githubusercontent.com/73579847/123125543-38d26f80-d466-11eb-85d5-17416e17a42e.jpg)
![repo7](https://user-images.githubusercontent.com/73579847/123125554-3bcd6000-d466-11eb-8bc3-3df4c3535f2b.jpg)
![repo8](https://user-images.githubusercontent.com/73579847/123125562-3d972380-d466-11eb-97f5-4407b3d3cc7f.jpg)
![repo9](https://user-images.githubusercontent.com/73579847/123125572-3ff97d80-d466-11eb-9756-936268211703.jpg)

# Step 6:
Then connect the instance and go to RDP client and download remote destop file
![repo10](https://user-images.githubusercontent.com/73579847/123125585-425bd780-d466-11eb-8df4-eb5ce24b9193.jpg)

# Step 7:
After connect to Remote Desktop, Create a text document name a.bat and save that file as a.bat
![repo11](https://user-images.githubusercontent.com/73579847/123133928-e301c580-d46d-11eb-9142-095007d325fd.jpg)
![repo12](https://user-images.githubusercontent.com/73579847/123133939-e6954c80-d46d-11eb-9d35-51a5b822224d.jpg)

# Step 8:
Then open that file multiple time, so that the CPU Utilization will increase
![repo14](https://user-images.githubusercontent.com/73579847/123133961-eb5a0080-d46d-11eb-894a-00381442a999.jpg)
![repo15](https://user-images.githubusercontent.com/73579847/123133969-edbc5a80-d46d-11eb-88a9-75889de0b314.jpg)

# Step 9:
Becasue our CPU Utilization cross 50% so that a new EC2 instance will create
![repo16](https://user-images.githubusercontent.com/73579847/123133980-f01eb480-d46d-11eb-9d3e-7dfe192103f0.jpg)






