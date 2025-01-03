# Master Image and Facial Recognition with AWS: Comprehensive Guide

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
7. [Screenshots](#)
8. [Useful Resources](#)          

> [!WARNING]
> Utilizing AWS services for this demo may lead to charges unless kept within [AWS Free Tier limits](https://aws.amazon.com/free/). Exceeding these limits incurs costs. Users can monitor their usage and set billing alerts via AWS tools to manage spending. Refer to "[Avoiding unexpected charges](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/checklistforunwantedcharges.html)" for advice on minimizing expenses.

## Project Overview
The scope of the demo is to build an application that provides us with a simple frontend (built using HTML and Bootstrap) to upload an image, a server running on EC2 - a virtual server on AWS, Amazon Rekognition - a powerful Machine Learning service on AWS.

The image analysis recognizes and lists the labels of an image - attribute (**Ex**. Scenery, Dance, Electronics, etc) and some facial attributes (if any) of the uploaded image.

## Pre-requisites

To deploy this application, you will need:

- An AWS account. If you don't have one, create it [here](https://aws.amazon.com) by following the on-screen instructions.
- IAM permissions to launch the necessary AWS services.
- A modern web browser.

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
Amazon Virtual Private Cloud (VPC) enables launching AWS resources in a customizable virtual network, providing control over IP addresses, subnets, and routing configurations.

- **AWS Identity and Access Management (IAM)**:
IAM secures AWS access management, allowing users to manage identities and permissions, controlling resource access.


## Frameworks/Libraries Used
- **Bootstrap v5**

A free and open-source framework for building the front end of applications.

Learn More: [Bootstrap](https://getbootstrap.com/)

- **aws-sdk v2 for JavaScript**

Enables the application to interact with AWS services programmatically.

**Example**: Listing all the buckets in our S3 account.

Learn More: [AWS SDK for JavaScript](https://docs.aws.amazon.com/sdk-for-javascript)

- **Express**

A Node.js framework used to serve the application and provide API endpoints for front-end functions.

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

### Step 4: Finish

For detailed instructions on each step, please refer to the comprehensive guide in the blog [here]().

# Screenshots
- ### Main Page
![Alt Text](https://github.com/sridurgeshv/AI-Project/blob/main/images/ss1.png)

- ### Result
![Alt Text](https://github.com/sridurgeshv/AI-Project/blob/main/images/ss2.png)

## Useful Resources
- [What is the AWS Free Tier, and how do I use it?](https://repost.aws/knowledge-center/what-is-free-tier)
- [How do I make sure I don't incur charges when I'm using the AWS Free Tier?](https://repost.aws/knowledge-center/free-tier-charges)
- [I unintentionally incurred charges while using the AWS Free Tier. How do I make sure that I'm not billed again?](https://repost.aws/knowledge-center/stop-future-free-tier-charges)
