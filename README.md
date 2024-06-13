# Image and Facial Analysis Demo Overview

## Table of Contents :-
1. [Pre-requisites](#)        
2. [Keywords](#)      
3. [AWS Services Used](#)         
4. [Resources Used](#)          
5. [Frameworks/Libraries Used](#)  
6. [Steps Overview](#)  
7. [Steps to Build the App](#)          
- Step 1: [Create an EC2 instance and an IAM role](#)         
- Step 2: [Connect to the EC2 Instance](#)         
- Step 3: [Install Node.js and Setup the Application](#)          
- Step 4: [Finish](#)          
8. [Additional Notes](#)          
9. [Screenshots](#)         
10. [Useful Resources](#)          

> [!WARNING]
> Utilizing AWS services for this demo may lead to charges unless kept within [AWS Free Tier limits](https://aws.amazon.com/free/). Exceeding these limits incurs costs. Users can monitor their usage and set billing alerts via AWS tools to manage spending. Refer to "[Avoiding unexpected charges](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/checklistforunwantedcharges.html)" for advice on minimizing expenses.

## Project Overview
The scope of the demo is to build an application that provides us with a simple frontend (built using HTML and Bootstrap) to upload an image, a server running on EC2 - a virtual server on AWS, Amazon Rekognition - a powerful Machine Learning service on AWS.

The image analysis recognizes and lists the labels of an image - attribute (Ex. Scenery, Dance, Electronics, etc) and some facial attributes (if any) of the uploaded image.

## Pre-requisites
To deploy the sample application you will require an AWS account. If you don’t already have an AWS account, create one at https://aws.amazon.com by following the on-screen instructions. Your access to the AWS account must have IAM permissions to launch the services that are used in this demo. To use the sample application you will require a modern browser.

### Keywords
- Javascript
- Express
- Node.js
- Machine Learning
- AWS SDK
- AWS Rekognition
- Face Detection
- Image Detection
- AWS IAM


## AWS Services Used
- **Amazon EC2**:
Amazon EC2 provides secure, scalable cloud computing, simplifying web-scale development with its intuitive web service interface. It offers extensive control over computing resources, leveraging Amazon's robust infrastructure. EC2 features a versatile compute platform with options for processors, storage, networking, OS, and pricing models. It delivers top-tier performance with fast processors, 400 Gbps ethernet, and specialized GPU instances for AI and graphics, alongside cost-effective inference instances.


- **Amazon Rekognition**:
Rekognition integrates image/video analysis into apps using advanced, scalable deep learning. It identifies objects, people, text, and activities in media without ML expertise, detects inappropriate content, and offers detailed facial analysis for user verification, crowd monitoring, and public safety.

- **Amazon VPC**:
Amazon Virtual Private Cloud (VPC) enables launching AWS resources in a customizable virtual network, offering users full control over IP addresses, subnet creation, and routing configurations. Supporting both IPv4 and IPv6, it enhances security and resource/application accessibility.

- **AWS Identity and Access Management (IAM)**:
IAM secures AWS access management. Users can manage identities and permissions via IAM, controlling resource access. It's a complimentary AWS feature; fees are incurred for other AWS services usage.

## Resources Used
- index.html: Markup for the static application
 
https://awsmc-dd.s3.ap-south-1.amazonaws.com/index.html

- index.js: Javascript logic for making API calls to the backend

https://awsmc-dd.s3.ap-south-1.amazonaws.com/index.js

- server.js: Backend logic which invokes the Amazon Rekognition service on the user’s behalf

https://awsmc-dd.s3.ap-south-1.amazonaws.com/server.js

- package.json: Dependency list for server.js

https://awsmc-dd.s3.ap-south-1.amazonaws.com/package.json

## Frameworks/Libraries Used
- **Bootstrap v5**
Bootstrap is a free and open-source framework for building the front end of the application.

Learn More: https://getbootstrap.com/

- **aws-sdk v2 for Javascript**
aws-sdk allows our application to access the AWS services on our behalf.

Example: Listing all the buckets in our S3 account

Learn More: https://docs.aws.amazon.com/sdk-for-javascript

- **Express**
A node.js framework to serve our application and to provide API endpoints for the frontend to invoke the functions to detect the labels and the facial expressions.

## Steps Overview
- Go to https://aws.amazon.com/console/
- Create an EC2 Instance (server) on AWS
- Configure the OS, Instance Type, Storage, Security, and other settings for your EC2 Instance.
- Assign permissions (through the IAM role) to your EC2 instance to access the Amazon Rekognition service.
- Launch the instance.
- Connect to the instance.
- In the terminal, type all the necessary commands, and once processed, your application will be ready to use.
- Copy the public IP address of your EC2 Instance and paste it into the new tab in the format <public ip>:3000 Example: http://43.204.79.72:3000
- You will be able to see the application running.
- Try uploading different images and inspect the response.

## Steps to Build the App
### Step 1: Create an EC2 instance and an IAM role
1. Go to [https://aws.amazon.com/console/](https://aws.amazon.com/console/)
2. After logging in, Navigate to the Console and select **“EC2”** from the services dropdown.
3. Click on **“Launch Instance”**
4. Select **Amazon Linux 2023** as the AMI
5. Select t3.micro type of instance and click on **“Next: Configure Instance Details”**
6. On this page (configure instance details or Step 3), we create an IAM role that gives **permissions** to the EC2 to access the AWS Rekognition service on your behalf. Click on **“Create a new IAM role”**
7. A new tab would be opened. Navigate to the new tab and click on on **“Create Role”**
8. Under “Choose a use case”, click on EC2 which would be under **“Common use cases”**
9. Now, we should attach the relevant permissions to our role. Search for **AmazonRekognitionFullAccess** and tick the box so that it will be attached to our role.
10. Click next and here you can optionally add tags.
11. Click next and assign a name to the role. I am going to assign the name as “aws-rekog-1”. Give a description and click **“Create Role”**.
12. Navigate to the previous tab, and click on the refresh button near **“Create new IAM role”**
13. Select the role that you just created. In my case it is aws-rekog-1. Now the IAM role field should look like this.
14. Click on **“Next: Add Storage”** and after that **“Next: Add Tags”** and then **“Next: Configure Security Groups”**. We will leave Storage and Tags as **defaults**.
15. In the security groups, Click on add a new rule and let the type of the new rule be **“Custom TCP Rule”**. Fill in the rule and finally, the rules should look as follows.
16. The new rule is going to allow us to access the EC2 instance from anywhere. We would be using the port number 3000 to host our application, but you can use any port number greater than 1024.
17. Click **“Review and Launch”**. Review your configuration and click on **Launch**.
18. A pop-up window will appear. Fill the form as below:
19. You can give any name to your key pair. Download the key pair and keep it safe. After that click on **Launch Instances**.

> [!NOTE]
> You can also proceed without creating a key pair for this demo.

### Step 2: Connect to the EC2 Instance
1. After the EC2 instance is created, connect to the EC2 instance by clicking on the **“Connect”** button. This will open an SSH connection to the EC2 instance.
2. A terminal should appear like shown below


### Step 3: Install Node.js and Setup the Application
1. **Install Node.js** by executing the following commands in the terminal
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh |
bash

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
nvm –version
nvm install node
```
2. Execute the following commands:
```bash 
mkdir app

cd app

mkdir public && mkdir server

cd public

wget https://awsmc-dd.s3.ap-south-1.amazonaws.com/index.html

wget https://awsmc-dd.s3.ap-south-1.amazonaws.com/index.js

cd ..

cd server

wget https://awsmc-dd.s3.ap-south-1.amazonaws.com/package.json

wget https://awsmc-dd.s3.ap-south-1.amazonaws.com/server.js

npm install
```
3. In point 4, steps a-c create the **directories**. Steps d-f involve navigating to the folder “public” and **downloading** index.html and index.js. Steps g-h involve navigating to the folder server and downloading **package.json and server.js**. Package.json contains the dependencies required by server.js. On doing **npm install**, those dependencies will be installed
4. Execute the following command in the terminal
```bash
node server.js
```
5. The above command will start the server and the terminal should look like below

### Step 4: Finish
You can find out the Public IP address of your EC2 Instance on the bottom left of the terminal window. OR you can find the Public IP address of the EC2 instance in the EC2 Management Console. On selecting the newly created instance, the public IP address will be shown in the properties of the selected EC2 instance.
Navigate to the browser and type the following:-
```bash
http://<IP_ADDDRESS>:3000
```
> [!NOTE]
> The <IP_ADDDRESS> will be the IP address that you found in the previous step. Example: http://43.204.79.72:3000

You would be able to see the webpage now. You have a working Image recognizer and the power of deep learning at your disposal. **Congratulations!**
