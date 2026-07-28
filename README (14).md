<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create S3 Buckets with Terraform

**Project Link:** [View Project](http://nextwork.ai/projects/aws-devops-terraform1)

**Author:** Folorunso Taiwo  
**Email:** folorunsotaiwo44@gmail.com

---

![Image](http://nextwork.ai/encouraged_silver_brave_blackcurrant/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use Terraform to provision and manage AWS infrastructure. The goal is to install and configure Terraform, authenticate with AWS, create and manage an Amazon S3 bucket using Infrastructure as Code (IaC), and upload files to the bucket using Terraform. This project showcases how Terraform simplifies infrastructure provisioning by making deployments consistent, automated, and easy to manage.


### Tools and concepts

The services I used were Terraform, AWS Identity and Access Management (IAM) for authentication, and Amazon S3 for object storage. Key concepts I learned include Infrastructure as Code (IaC), using Terraform providers and resource blocks, managing cloud infrastructure with configuration files, initializing, planning, and applying infrastructure changes, and automating the creation and management of AWS resources in a consistent and repeatable manner.


### Project reflection

This project took me approximately 3 hours to complete. The most challenging part was troubleshooting the Terraform provider initialization and resolving the temporary DNS issue encountered during `terraform apply`. It was most rewarding to successfully provision an Amazon S3 bucket, upload an image using Terraform, and see the infrastructure managed entirely through Infrastructure as Code.


I chose to do this project today because I wanted to strengthen my Terraform skills and gain hands-on experience with Infrastructure as Code by automating the deployment and management of AWS resources. Something that would make learning with NextWork even better is providing more real-world scenarios, additional troubleshooting guidance for common errors, and more advanced project extensions to reinforce practical cloud engineering skills.


---

## Introducing Terraform

Terraform is is a tool that help you build and manage your cloud inftrastructure using code, instead of manually setting up your resources in aws, you write a script that tells terraform exactly what you want in your cloud infrastructure like servers, databases and networks, terraform then build all of these for you using your script as the blueprint.

Infrastructure as Code (IaC) is the practice of describing your cloud setup (like your servers, storage, networks) in plain text files instead of clicking through a web console. When you run those files, the cloud builds everything exactly as you've written it written. Because the description lives in code, you can version-control it, share it with teammates, and recreate the same environment any time you need.

Terraform uses configuration files to define and manage infrastructure as code. The main.tf file is the primary configuration file where the infrastructure resources, provider settings, and other Terraform configurations are defined. It serves as the main blueprint that Terraform uses to provision and manage resources in AWS.

![Image](http://nextwork.ai/encouraged_silver_brave_blackcurrant/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Configuration files

The configuration is structured in Terraform blocks, including a provider block that specifies the AWS region and resource blocks that define the S3 bucket and its public access settings. The advantage of doing this is that the infrastructure is defined as code, making it easy to automate, version, modify, and deploy consistently across different environments.

### My main.tf configuration has three blocks

The first block indicates the AWS provider and specifies the region where the resources will be created. The second block provisions an Amazon S3 bucket with a globally unique name. The third block manages the bucket's public access settings by blocking public access, helping to improve the security of the S3 bucket.

![Image](http://nextwork.ai/encouraged_silver_brave_blackcurrant/uploads/aws-devops-terraform1_ljvh9876)

---

## Customizing my S3 Bucket

For my project extension, I visited the official Terraform documentation to learn more about the AWS S3 bucket resource and its available configuration options. The documentation shows the syntax, required and optional arguments, example configurations, and additional settings that can be used to customize and manage S3 buckets with Terraform.

I chose to customize my bucket by adding tags because they help identify, organize, and manage AWS resources more effectively. Tags are commonly used for resource management, cost allocation, and ownership tracking. When I launch my bucket, I can verify my customization by opening the bucket in the AWS Management Console and checking the Tags section to confirm that the tags have been applied successfully.

![Image](http://nextwork.ai/encouraged_silver_brave_blackcurrant/uploads/aws-devops-terraform1_ffe757cd3)

---

## Terraform commands

I ran `terraform init` to initialize my Terraform working directory. This command downloaded the required AWS provider plugin, prepared the backend, and set up the project so Terraform could manage my infrastructure based on the configuration in `main.tf`.


Next, I ran `terraform plan` to preview the changes Terraform would make to my AWS environment based on the configuration in `main.tf`. This allowed me to verify that the correct resources would be created and review the execution plan before applying any changes.


![Image](http://nextwork.ai/encouraged_silver_brave_blackcurrant/uploads/aws-devops-terraform1_3g4h5i6j)

---

## AWS CLI and Access Keys

Using existing local AWS CLI configuration

The AWS Command Line Interface (AWS CLI) is a tool that allows users to interact with and manage AWS services directly from the command line. It enables users to create, configure, update, and delete AWS resources using commands instead of the AWS Management Console, making automation, scripting, and infrastructure management more efficient.


I set up AWS access keys to securely authenticate the AWS CLI and Terraform with my AWS account. This allows them to make authorized API calls to create, manage, and delete AWS resources without requiring me to sign in through the AWS Management Console each time.


![Image](http://nextwork.ai/encouraged_silver_brave_blackcurrant/uploads/aws-devops-terraform1_7j8k9l0m)

---

## Lanching the S3 Bucket

I ran `terraform apply` to provision the AWS resources defined in my `main.tf` configuration file. Running `terraform apply` will affect my AWS account by creating the specified S3 bucket and configuring its public access settings and tags, making the desired infrastructure changes in accordance with the Terraform configuration.


The sequence of running `terraform init`, `terraform plan`, and `terraform apply` is crucial because each command prepares for the next. `terraform init` initializes the working directory and downloads the required provider plugins; `terraform plan` previews the infrastructure changes and verifies the configuration; and `terraform apply` provisions the resources in AWS. Following this sequence helps ensure the configuration is validated, the planned changes are reviewed, and the infrastructure is deployed accurately and safely.


![Image](http://nextwork.ai/encouraged_silver_brave_blackcurrant/uploads/aws-devops-terraform1_1q2w3e4r)

---

## Uploading an S3 Object

I created a new resource block to define an Amazon S3 object that uploads a local image file to my S3 bucket. This allows Terraform to manage both the bucket and the uploaded object as part of the same Infrastructure as Code configuration, ensuring they can be deployed and managed consistently.


I need to run `terraform apply` again because the Terraform configuration was updated with a new resource. Running `terraform apply` compares the updated configuration with the current infrastructure state and provisions only the new changes, ensuring the AWS environment matches the latest Terraform configuration.


To validate that I've updated my configuration successfully, I ran terraform apply and confirmed that the new aws_s3_object resource was created successfully. I then verified the upload by opening my S3 bucket in the AWS Management Console and confirming that image.png appeared in the bucket's Objects tab.

![Image](http://nextwork.ai/encouraged_silver_brave_blackcurrant/uploads/aws-devops-terraform1_9o0p1a2s)

---

---
