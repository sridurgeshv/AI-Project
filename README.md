# Image and Facial Analysis Demo Overview

## Table of Contents :-
1. [Pre-requisites](#)        
2. [Keywords](#)      
3. [AWS Services Used](#)              
4. [Frameworks/Libraries Used](#)  
5. [Steps Overview](#)  
6. [Steps to Build the App](#)          
- Step 1: [Create an EC2 instance and an IAM role](#)         
- Step 2: [Connect to the EC2 Instance](#)         
- Step 3: [Install Node.js and Setup the Application](#)          
- Step 4: [Finish](#)          
7. [Additional Notes](#)          
8. [Screenshots](#)         
9. [Useful Resources](#)          

> [!WARNING]
> Utilizing AWS services for this demo may lead to charges unless kept within [AWS Free Tier limits](https://aws.amazon.com/free/). Exceeding these limits incurs costs. Users can monitor their usage and set billing alerts via AWS tools to manage spending. Refer to "[Avoiding unexpected charges](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/checklistforunwantedcharges.html)" for advice on minimizing expenses.

## Project Overview
The scope of the demo is to build an application that provides us with a simple frontend (built using HTML and Bootstrap) to upload an image, a server running on EC2 - a virtual server on AWS, Amazon Rekognition - a powerful Machine Learning service on AWS.

The image analysis recognizes and lists the labels of an image - attribute (**Ex**. Scenery, Dance, Electronics, etc) and some facial attributes (if any) of the uploaded image.

## Pre-requisites
To deploy the sample application you will require an AWS account. If you don’t already have an AWS account, create one at [Here](https://aws.amazon.com) by following the on-screen instructions. Your access to the AWS account must have IAM permissions to launch the services that are used in this demo. To use the sample application you will require a modern browser.

## Keywords
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
Amazon Elastic Cloud Compute (EC2) is a cloud service providing scalable and secure computing power. It allows users to run applications and manage servers without owning physical hardware, making it cost-effective and flexible for various computing needs.

- **Amazon Rekognition**:
Rekognition integrates image/video analysis into apps using advanced, scalable deep learning. It identifies objects, people, text, and activities in media without ML expertise, detects inappropriate content, and offers detailed facial analysis for user verification, crowd monitoring, and public safety.

- **Amazon VPC**:
Amazon Virtual Private Cloud (VPC) enables launching AWS resources in a customizable virtual network, offering users full control over IP addresses, subnet creation, and routing configurations. Supporting both IPv4 and IPv6, it enhances security and resource/application accessibility.

- **AWS Identity and Access Management (IAM)**:
IAM secures AWS access management. Users can manage identities and permissions via IAM, controlling resource access. It's a complimentary AWS feature; fees are incurred for other AWS services usage.


## Frameworks/Libraries Used
- **Bootstrap v5**

Bootstrap is a free and open-source framework for building the front end of applications.

Learn More: [Bootstrap](https://getbootstrap.com/)

- **aws-sdk v2 for JavaScript**

The AWS SDK for JavaScript allows our application to interact with AWS services programmatically.

**Example**: Listing all the buckets in our S3 account.

Learn More: [AWS SDK for JavaScript](https://docs.aws.amazon.com/sdk-for-javascript)

- **Express**

Express is a Node.js framework used to serve our application and provide API endpoints for the front end to invoke functions, such as detecting labels and facial expressions.

Learn More: [Express](https://expressjs.com/)

## Steps Overview
- Go to the [AWS Console](https://aws.amazon.com/console/)
- Create an EC2 Instance (server) on AWS
- Configure the settings for your EC2 Instance, including: - Operating System (OS), Instance Type, Storage & Security.
- Assign an IAM role to your EC2 instance with permissions to access the Amazon Rekognition service.
- Launch the instance.
- Connect to the instance.
- In the terminal, type all the necessary commands, and once processed, your application will be ready to use.
- Copy the public IP address of your EC2 Instance and paste it into a new browser tab in the format `<public-ip>:3000`. **Example**: `http://54.80.238.206:3000`
- You will see the application running.
- Try uploading different images and inspect the response.

## Steps to Build the App
### Step 1: Create an EC2 instance and an IAM role

### Step 2: Connect to the EC2 Instance

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
