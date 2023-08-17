# [Purpose of Deployment]

* To deploy a web application using AWS Elastic Beanstalk.

# [Description]

This project began diagramming the plan for my deployment in Draw.io including how I would use **GitHub**, **Jenkins**, and **AWS Elastic Beanstalk**. I continued to plan and build within a previously created Jenkins account by my instructor. Jenkins allowed me to create and test my deployment in a staging environment to ensure that it would return a 200 response from the server once deployed. Once my build passed the test phase in Jenkins, I created IAM roles and an EC2 instance through Elasticn Beanstalk. This allowed AWS access with the necessary permissions to update and launch my deployment through the IAM roles of **AWSElasticBeanstalkWebTier** and  **AWSElasticBeanstalkMulticontainerDocker**. Finally, the EC2 instance createed an applicable production environment to deploy my web applicaiton successfully. 

###### [Below you will find the necessary steps that I took to test and deploy my web applicaiton, as well as some drawbacks that I was able to rectify along the way:] 

1. Diagram the plan for deployment on Draw.io:
![Diagram of Deployment 1 1](https://github.com/DANNYDEE93/Deployment1.1D/assets/140758597/48dfdcfa-d239-4aa1-a4a5-2289cc09375b)


2. Log into GitHub account
3. Create new GitHub repository
4. Create **Documentation.md** file to record the staging and production environment of deployment
5. Open Kura Labs c4 Deployment-1 repository and follow the provided instructions:
   https://github.com/kura-labs-org/c4_deployment-1/blob/main/Deployment-instructions.md
6. Press the **Code** tab and download files from Kura Labs repository
7. Unzip files by extracting Kura Lab files from the folder populated in your terminal in order for them to upload properly onto your GitHub repository 
8. Upload Kura Lab repository files into new GitHub repository created in **Step 3**

**9. [Create Build in Jenkins:]**

10. Sign into your Jenkins account
11. Press **New Item** tab to create new pipeline build
12. Name pipeline "First name, Last name initial"
13. Select Pipeline script from SCM
14. Choose Git in the dropdown from SCM
15. Go back to newly created GitHub repository and copy the HTTP code or URL of the repository
16. Paste code into "Repsitory line" in Jenkins

**17. [Create token for Jenkins using GitHub account:]**

18. Go back to your GitHub and press profile picture/icon
19. Select **Settings**-->**Developer Settings**-->**Personal Access Tokens**--> **Tokens(classic)**
20. Select **Generate new token**-->**Generate new token (classic)**-->Sign into GitHub if prompted
21. Create note description-->Select scopes: **repo** and **admin repo** to give full access to repository.
22. Click **Generate token**--> Copy and past link into **password line** in Jenkins
23. Continue on Jenkins-->Add token associated with repository--> Select main branch
24. Submit to generate build and select **Build Now** and pass staging environment in Jenkins

**[Drawback #1]:**

My multiple attempts to download onto Jenkins were unsuccessful because my copied Jenkinsfile was saved as a **.txt** file that was blocking Jenkins from reading the file's code properly. Once I deleted **.txt** off the file, my build passed the test stage on Jenkins. 

[[Download GitHub Repository to unzip files and re-zip them to upload onto AWS Elastic Beanstalk]]

25. Create zip file folder your File Explorer **[Windows OS]** to compress your GitHub repository. This new compressed zip file should not exceed 500 MB and should not include parent folder from your original repository to ensure that all characters in file are configured correctly in Elastic Beanstalk. You will need to extract files from the folder and create a new compressed zip file like in **Step 7**
26. Select files within the downloaded file of your repository and transfer them into a new compressed zip folder. This ensures that the files are zipped to Elastic Beanstalk's standards

[[After checking the console output responses and passing the test phase in Jenkins, you can go on to creating **IAM Roles** and the **Python Url Shortener** through **AWS Elastic Beanstalk**]]

**[27.Navigating throguh AWS Elastic Beanstalk]**

[Create **IAM Roles**]

28. Sign into AWS with appropriate Account ID, IAM user name, and password
    
29. Select **Roles** in Dashboard--> Click **Create role**--> Select **AWS service** for trusted entity type--> Under the dropdown for AWS Services: Select **Elastic Beanstalk**--> Select **Customizable** option under cases to give Elastic Beanstalk permission to manage AWS resources of your deployment--> Click **Next**--> Click **Next**--> Enter **AWS-Elasticbeanstalk-service-role** in Role name--> "Create Role
    
30. To create the second and third role: Click **Create Role**--> Select **AWS service** for trusted entity type--> Click **EC2** under common use cases--> Click Next--> Under Permission policies: Select **AWSElasticBeanstalkWebTier** and **AWSElasticBeanstalkMulticontainerDocker**--> Click Next--> Enter **Elastic-EC2** in **Role name** field--> Click **Create Role**
    
[These roles allow the instances in your web server environment to access and upload necessare files and grants permissions for Amazon Elastic Container Service to organize and cluster task within container environments.]

[Create and deploy a **Python URL shortener**]

31. Select **Create Application**--> Name application **URL-shortener**--> Select **Python** in Platform dropdown--> Select **Python 3.9 running on 64bit Amazon Linux 2023** in Platform branch dropdown-->Select **Upload your code**--> Type **V1** in version label field--> [Choose and upload the compressed zip file of your repository]-->Click **Next**
32. Select **ElasticEC2** in EC2 instance profile dropdown--> Click **Next**--> Select default VPC in VPC dropdown--> Select **us-east-1a** availability zone--> Click **Next**--> Select **General Purpose (SSD)** in Root Volume type drop down--> Change the size field to 10GB-->Select **ONLY "T2.MICRO"** under **Instance Types** and **DESELECT** any other choices--> Click **Next**--> Click **Next**--> Click **Submit**
    
[The URL shortener reduces the number of characters in a URL so that it is easier for Elastic Beanstalk to read, remember, and share your web service and application. AWS Elastic Beanstalk makes it easier for developers to quickly depoly and manage these applications.]

33. **Upload and Deploy** your compressed zip file on Elastic Beanstalk. You will know that you passed once the **health status reads "OK"** and you get a response that your deployment has uploaded successfully to your EC2 instance.

**[Drawback #2]:**

Although, I downloaded a zip file from my repository. This file was not uploading succesfully and the health of my deployment kept changing to "Degraded" because it was not compressed enough to Elastic Beanstalk requirements. After multiple attempts, I found out that I needed to create a completely new compressed zip file with only the files within the downloaded zip file. Only then, was i able to complete my first successful deployment. **Pay close attention to Steps 25 & 26** 

[Screenshots of my successful deployment on AWS Elastic Beanstalk]

![Screenshot_Deployment 1](https://github.com/DANNYDEE93/Deployment_DD/assets/140758597/0fb109e5-b273-4881-8fb5-6dbbf8c413d5)

![Screenshot_Deployment 2](https://github.com/DANNYDEE93/Deployment_DD/assets/140758597/9791a8c8-02fe-4462-9ff4-80e370aaa15b)

