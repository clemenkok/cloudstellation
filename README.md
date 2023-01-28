# Cloudstellation: A Repository of AWS Projects

> What will 2023 bring?
> 
> Prediction 1: Cloud technologies will redefine sports as we know them  
> Prediction 2: Simulated worlds will reinvent the way we experiment  
> Prediction 3: A surge of innovation in smart energy  
> Prediction 4: The upcoming supply chain transformation  
> Prediction 5: Custom silicon goes mainstream  
> 
**- All Things Distributed**

Each project in Cloudstellation will include an architecture diagram (created with [draw.io](https://app.diagrams.net/)) and a quick overview of the steps needed to build out the architecture. Cloudstellation will contain projects ranging across the spectrum of applications, including networking (VPC peering, DNS configuration), machine learning (Rekognition + ECS, MLOps Pipeline), serverless (lambda + api gateway).

Why did I do this? I had completed the Solutions Architect Associate (SAA-C03) Certification and was looking around for projects to further my practical skills before my internship, as well as to apply for research computing positions. Some of these projects could be useful as well for someone starting out in AWS, so I might as well document it.  
<br/><br/>
## Project I: Cloud Resume Challenge
### S3, Route53, CloudFront, SAM, DynamoDB, Lambda, API Gateway
![cloudresume_one](https://user-images.githubusercontent.com/68755138/214983805-18d28316-e6b5-4f68-a438-2a2b65a1cb5f.png)

The objective of this project is to build a resume website using several AWS services. It is based off of the [challenge](https://cloudresumechallenge.dev/) created by Forrest Brazeal.  

The challenge can be broken down into multiple stages.  

> Stage 1: Cloud Website
> Skills: HTML/CSS, Git, cloud storage, CDN, DNS
> 
> Stage 2: Serverless API
> Skills: Cloud compute, NoSQL database, Python
> 
> Stage 3: Front End / Back End Integration
> Skills: Javascript, cloud monitoring, end-to-end testing
> 
> Stage 4: Infrastructure as Code and CI/CD
> Skills: Terraform, GitHub Actions, cloud secrets management  

Using this challenge as a guide, I created my own [website](clemenkok.com) where I wrote about my portfolio and past experiences.  

Some key things that I learnt while building this project:  

- When using Amazon-generated SSL Certificates, infrastructure must be deployed on ```us-east-1 (N. Virginia)``` - this is an inherent limitation of Amazon-generated SSL Certificates. As I had initially used another zone, I had to restart my project on ```us-east-1```.  

- I used the AWS SAM CLI for this project, allowing me to deploy my Infrasturucture as Code. This was extremely useful and efficient and I no longer had to click around the console. AWS SAM is a wrapper around CloudFormation, AWS' IaC service.  
<br/><br/>
## Project II: Learn Cantrill Lab: Video on Demand
### S3, Lambda, API Gateway, MediaConvert, CloudFront
![estets drawio](https://user-images.githubusercontent.com/68755138/215002848-21961626-7db1-48f4-9d44-26d464d61344.png)

The objective of this project is to create a pipeline for a .mp4 video file to be converted into HD and SD and then output it onto a CloudFront Distribution.  

It is based off of [Adrian Cantrill's Lab Projects](https://github.com/acantril/learn-cantrill-io-labs). It is a relatively simple project that is a good introduction to AWS.  
<br/><br/>
## Project III: Learn Cantrill Lab: Serverless Reminder Application
### S3, SES, API Gateway, Lambda, Step Functions
The architecture for this project can be found [here](https://github.com/acantril/learn-cantrill-io-labs/tree/master/aws-serverless-pet-cuddle-o-tron).  

Some things that I learnt from this project:  
- Creating a [State Machine](https://docs.aws.amazon.com/step-functions/latest/dg/amazon-states-language-state-machine-structure.html) in AWS using Step Functions. This is a pretty neat feature. In the project, you create a state machine that includes a timer state, which delays the trigger of the email Lambda function until the time specified has passed and then send the email. This was my first time using Step Functions and served as a good introduction.
- SES. Emailing a user is, as the name implies, simple.
<br/><br/>
## Project IV: Learn Cantrill Lab: Cat/Dog Recognition App
### Rekognition, ECS, ECR
![rekk drawio](https://user-images.githubusercontent.com/68755138/215192282-a539a7c8-53e8-4bd6-8bf6-4a0006e6895c.png)

The objective of this project is to build an application that can distinguish between a dog and a cat.  

The workflow is as such: A user accesses the public IP exposed by ECS and uploads an image containing a cat or dog onto the platform. ECS is running a Docker image that we upload on ECR, which contains a Flask application that can call Rekognition to perform inference using our trained model. It then outputs the result onto the screen.
<br/><br/>
## Project IV: Docker-based Flask App with Aurora Serverless
### RDS, Secrets Manager, Docker

The objective of this project is to create a Docker-based application that interacts with an Aurora serverless instance. Using Flask, we set up some APIs which then can be used to get data from our Aurora Serverless Database. 

