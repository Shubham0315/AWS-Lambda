# AWS-Lambda
Serverless application leveraging AWS Lambda for efficient, scalable event-driven processing with seamless GitHub integration

- On day to day basis, we use lambda for Cloud Cost optimization which is primary responsibility as devops engineer. 
- We can trigger lambda functions with wide range of services like S3, cloudwatch and perform activities known as "Event friven Actions"

- Lambda function solves problem of compute and serverless. It belongs to same family of EC2 compute.
- Lambda function gives us compute like EC2
  - We can run our application on the lambda compute just like EC2. Lambda follows serverless architecture only difference from EC2. AWS will take care of server depending on app we're running.
  - After creating lambda function specifying all the requirements for instance, AWS will automatically take care of server depending on application we're running.
  - AWS create compute for us and once entire application is triggered, it will create compute. Once lambda fucntion is completed, AWS will pair down the compute.
  - In lambda, we dont need to tell AWS about CPU, RAM. AWS will automatically create compute instance for us.
  - Here in serverless architecture, we're not responsible for server at all.
  - If our app need more CPU or increase RAM, we dont need to tell to AWS, lambda it will create the instance and automatically scale the instance.
  - Once task is done, it will scale it down.
 
- Lets say we have food delivery app. User created requests for some specific food. He goes to checkout and does payment. Once transaction is done, he will move out of app and his order is placed.
  - To use lambda for this activity, when user sends request, AWS creates infrastructure for running the app. After transaction request is fulfilled by user, AWS will take down the infrastructure it created. This is advantage of using "Serverless Architecture"
  - EC2 is pay as you go, we need to manage it in auto scale, scale down by ourselves. In lambda, no need to take care of server
 
- While creating EC2 we get IP address. In Lambda we dont get same. We dont even know where EC2 is hosted. Means we cannot see detailed architecture of lambda.
- As devops engineer, we dont decide to go with server or serverless approach. It decided by dev, architecture team as it depends on application written.

- As devops engineer, when someone tells to create lambda function or create infrastructure we need to take care of the same.
  - We can make use of lambda for cost optimization
 
- In cost optimization project, if developer has created EBS volume 30 days ago and no one is using it, we can send out notification to team that it is costing organization.
- Using lambda functions we can take look at all AWS resources that our organization is using and we can report them writing a script to govern resource usage, to check if any unused resource is consuming cost.

- Lets say we have written 10 python scripts for the activity or 10 lambda functions. This activity is to be done everyday at 10am. So we'll run script everydayat that time. If we use EC2, we need to create EC2 every morning, if script runs for 5 mins, after that delete EC2.
  - With lambda, we need to tell AWS cloudwatch, everyday at 10 am trigger the lambda function as lambda is event driven. It will create EC2, run scripts and delete EC2 after that. So we dont need to bother about cost.
 
Used of Serverless Architecture
-
- Cost optimization
- To take care of security and compliance
- Perform routine activities

- **Use case** :- If our organization decides no one will create EBS volume of GP2 type as it is compliance/security issue. Here we can write lambda functions to run everyday at 10 am to verify if there is any GP2 based EBS volume and trigger notification to team using SNS service to delete as this is against compliance.

- We can do endless things with lambda.

---------------------------------------------------------------------------------------------------------------------

Practical Demo
-
- Go to lambda - Create function - Provide name - Select runtime
- In advanced settings, enable function URL to get public IP to access application written in lambda function
- In auth type, select "NONE" to allow access to anyone
- Create function

![image](https://github.com/user-attachments/assets/23610379-84db-4c5e-83b8-b9c22f06ce3d)
![image](https://github.com/user-attachments/assets/e1f8cdf8-00ff-4f63-b46e-c85f8d61c688)

- We can see function got created with 2 options :-  Add trigger and Add destination

![image](https://github.com/user-attachments/assets/6af5bbbf-aa79-496a-aea7-5b6c22faed2e)

  - As lambda functions are event driven, triggered by events
  - Without option of trigger we need to manually write/run lambda function which kills idea of serverless architecture.


  
