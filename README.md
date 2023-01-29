# Cloudstellation: A Repository of AWS Projects
<br/><br/>
> What will 2023 bring?
> 
> Prediction 1: Cloud technologies will redefine sports as we know them  
> Prediction 2: Simulated worlds will reinvent the way we experiment  
> Prediction 3: A surge of innovation in smart energy  
> Prediction 4: The upcoming supply chain transformation  
> Prediction 5: Custom silicon goes mainstream  
> 
**- All Things Distributed**

Each project in Cloudstellation will include an architecture diagram (created with [draw.io](https://app.diagrams.net/)) and a quick overview of the steps needed to build out the architecture. Cloudstellation will contain projects ranging across the spectrum of applications, including networking, machine learning and serverless. 

Why did I do this? I had completed the Solutions Architect Associate (SAA-C03) Certification and was looking around for projects to further my practical skills before my internship, as well as to apply for research computing positions. Some of these projects could be useful as well for someone starting out in AWS, so I might as well document it.  

[Project I: Cloud Resume Challenge](#1)  
[Project II: Video on Demand](#2)  
[Project III: Serverless Reminder Application](#3)  
[Project IV: Cat/Dog Recognition App](#4)  
[Project V: Docker-based Flask App with Aurora Serverless](#5)  
[Project VI: Web Scraper with Boto3 and SNS](#6)  
[Project VII: StockWatch](#7)  
[Project VIII: Covid 19 ETL](#8)  
[Project IX: Build, Test and Deploy ETL solutions using AWS Glue and AWS CDK based CI/CD pipelines](#9)  
[Project X: Extracting buildings and roads from AWS Open Data using Amazon SageMaker](#10)  
[Project XI: Stock Market Analysis Pipeline](#10)  
[Project XII: AWS EMR and Pyspark with Ubisoft Open Data](#11)  

<br/><br/>
## <a name="1">Project I: Cloud Resume Challenge</a>
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

- CI/CD. Stages: (1) Testing Infrastructure (functions that you have written to get/put data in DynamoDB), (2) On successful test build and deploy infrastructure, (3) afterwards deploy the site (changes to site i.e. website code).

<br/><br/>
## <a name="2">Project II: Learn Cantrill Lab: Video on Demand</a>
### S3, Lambda, API Gateway, MediaConvert, CloudFront
![estets drawio](https://user-images.githubusercontent.com/68755138/215002848-21961626-7db1-48f4-9d44-26d464d61344.png)

The objective of this project is to create a pipeline for a .mp4 video file to be converted into HD and SD and then output it onto a CloudFront Distribution. 

It is based off of [Adrian Cantrill's Lab Projects](https://github.com/acantril/learn-cantrill-io-labs). It is a relatively simple project that is a good introduction to AWS. I have completed a few more of Cantrill's labs below - one gripe was that it was mostly console-based so I lacked familiarity with IaC that was used in Project I. 
<br/><br/>
## <a name="3">Project III: Learn Cantrill Lab: Serverless Reminder Application</a>
### S3, SES, API Gateway, Lambda, Step Functions
The architecture for this project can be found [here](https://github.com/acantril/learn-cantrill-io-labs/tree/master/aws-serverless-pet-cuddle-o-tron).  

Some things that I learnt from this project:  
- Creating a [State Machine](https://docs.aws.amazon.com/step-functions/latest/dg/amazon-states-language-state-machine-structure.html) in AWS using Step Functions. This is a pretty neat feature. In the project, you create a state machine that includes a timer state, which delays the trigger of the email Lambda function until the time specified has passed and then send the email. This was my first time using Step Functions and served as a good introduction.
- SES. Emailing a user is, as the name implies, simple.
<br/><br/>
## <a name="4">Project IV: Learn Cantrill Lab: Cat/Dog Recognition App</a>
### Rekognition, ECS, ECR
![rekk drawio](https://user-images.githubusercontent.com/68755138/215192282-a539a7c8-53e8-4bd6-8bf6-4a0006e6895c.png)

The objective of this project is to build an application that can distinguish between a dog and a cat.  

The workflow is as such: A user accesses the public IP exposed by ECS and uploads an image containing a cat or dog onto the platform. ECS is running a Docker image that we upload on ECR, which contains a Flask application that can call Rekognition to perform inference using our trained model. It then outputs the result onto the screen.
<br/><br/>
## <a name="5">Project V: Docker-based Flask App with Aurora Serverless</a>
### RDS, Secrets Manager, Docker

The objective of this project is to create a Docker-based application that interacts with an Aurora serverless instance. Using Flask, we set up some APIs which then can be used to get data from our Aurora Serverless Database. It is from this [tutorial](https://www.youtube.com/watch?v=NM4Vd7fpZWk&t=10s).  

Note: Aurora Serverless V2 has no Data API, which is needed for this project.
<br/><br/>
## <a name="6">Project VI: Web Scraper with Boto3 and SNS</a>
### SNS
This project involves scraping Bestbuy's website using Boto3. If the quantity of the item exceeds a certain amount, the scraper script publishes to a SNS topic, which then sends an email to a user that their item is available. It is from this [tutorial](https://www.youtube.com/watch?v=6ixBJZ2vnYk&t=419s).
<br/><br/>
## <a name="7">Project VII: StockWatch</a>
### DynamoDB, Lambda, SNS, CloudWatch, AppConfig

![stox drawio (1)](https://user-images.githubusercontent.com/68755138/215293978-d68cfa14-c69c-4b7b-99b1-9f409bd54468.png)

This project is from [Be a Better Dev](https://www.youtube.com/watch?v=XoMSzGybxZg&t=311s). He did not upload a part 2 so I prepared the code and infrastructure unguided.

What I learnt:
- When writing my ```.yaml``` file to describe my infrastructure, I learnt about intrinsic functions and how we ahve to use intrinsic functions to pass certain data around (as ARNs have not been generated). 
- Importance of iterative development: develop one stage at a time. I eventually decided to try a simpler project first (see below) before coming back to this. (Also, I should label my architecture...)
<br/><br/>
## <a name="8">Project VIII: A Cloud Guru Challenge - Covid 19 ETL</a>
### Serverless Framework, EventBridge, Lambda, DynamoDB, S3, SNS, Athena, QuickSight
![covid drawio (1)](https://user-images.githubusercontent.com/68755138/215298522-7be255fc-c3b3-4893-8160-66ef8200be58.png)

This project is from Forrest Brazeal's A Cloud Guru Challenge on automating a Covid 19 ETL pipeline. In building this I used the Serverless Framework, which was an extremely useful resource to build event-driven applications.  

A ```cron``` job was scheduled on EventBridge to trigger an endpoint every day at a fixed time. This endpoint would be a Lambda Function, which handles the ETL. API Calls are made to the New York Times and Johns Hopkins University COVID-19 Data API, which is returned as a CSV file. They are converted into Pandas DataFrames. Transformation then occurs, with the data being processed by removing nullification and joining the dataframes together. Subsequently the data is loaded into S3, which feeds into a Glue workflow (in between, checks are created to ensure that data is not lost if the ETL process fails. The user is also updated on the ETL progress through SNS). Glue automatically feeds into Athena. Using QuickSight, we import the Athena data, enabling it to be dashboarded. 
<br/><br/>
## <a name="9">Project IX: Build, Test and Deploy ETL Solution with Glue and CDK-based CI/CD Pipelines</a>
### CodeBuild, CodeCommit, CodePipeline, Glue, S3, Athena
<< To be Added >>
<br/><br/>
## <a name="10">Project X: Extracting buildings and roads from AWS Open Data using Amazon SageMaker</a>
### SageMaker, AWS Open Data
<< To be Added >>
<br/><br/>
## <a name="11">Project XI: Stock Market Pipeline and Forecasting with LSTM</a>
### Lex, Lambda, S3
<< To be Added >>
## <a name="12">Project XII: AWS EMR and Pyspark with Ubisoft Open Data</a>
### EMR
<< To be Added >>
