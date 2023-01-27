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

Each project in Cloudstellation will include an architecture diagram and a quick overview of the steps needed to build out the architecture.  

Why did I do this? I had completed the Solutions Architect Associate (SAA-C03) Certification and was looking around for projects to further my practical skills before my internship, as well as to apply for research computing positions. Some of these projects could be useful as well for someone starting out in AWS, so I might as well document it.  

## Project I: Cloud Resume Challenge

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

