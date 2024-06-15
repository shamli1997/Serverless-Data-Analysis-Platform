# Project 2: Serverless Data Analysis Platform

## Overview

Project 2 revolves around crafting a cutting-edge serverless data analysis platform. This platform empowers Lambda functions to access and analyze data from both a public RDS database and a private RDS database, with the results elegantly stored in an S3 bucket.

## Key Components

1. **Amazon RDS**:
   - **Public RDS**: A publicly accessible RDS database.
   - **Private RDS**: A privately accessible RDS database within a VPC.

2. **AWS Lambda**:
   - **Data Analysis**: Lambda functions perform data analysis by accessing the RDS databases.

3. **Amazon S3**:
   - **Storage**: Results of the data analysis are stored in an S3 bucket for further use.

4. **VPC and Subnets**:
   - **Network Configuration**: VPC setup to include both public and private subnets to manage RDS access.

## Architecture Diagrams

### Publicly Accessible RDS

![Publicly Accessible RDS](https://github.com/shamli1997/Serverless-Data-Analysis-Platform/blob/main/Public_RDS.png)

#### Explanation
This diagram illustrates how a publicly accessible RDS instance can be accessed:

1. **Client**: Represents the user or application trying to access the RDS instance.
2. **Firewall**: Ensures secure communication by allowing or blocking specific traffic.
3. **Internet Gateway**: Provides a path for communication between the client and the RDS instance over the internet.
4. **VPC**: Virtual Private Cloud that contains the public subnet.
5. **Public Subnet**: A subnet that is accessible from the internet.
6. **Security Group**: Acts as a virtual firewall for the RDS instance to control inbound and outbound traffic.
7. **Amazon RDS DB Instance**: The actual RDS database instance that is publicly accessible.
   
## Video Walkthrough

Here's a walkthrough of implemented features:

<img src='https://github.com/shamli1997/Serverless-Data-Analysis-Platform/blob/main/public-rds-1.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

### Privately Accessible RDS

![Privately Accessible RDS](https://github.com/shamli1997/Serverless-Data-Analysis-Platform/blob/main/Private_RDS.png)

#### Explanation
This diagram illustrates how a privately accessible RDS instance is accessed within a VPC:

1. **AWS Cloud**: Represents the AWS infrastructure.
2. **VPC**: Virtual Private Cloud that contains the private subnet.
3. **Private Subnet**: A subnet that is not accessible from the internet.
4. **Lambda Function**: Executes code that needs access to the RDS instance.
5. **RDS DB Instance**: The actual RDS database instance that is privately accessible.
6. **Security Group**: Controls the inbound and outbound traffic for the Lambda function and RDS instance.

## Video Walkthrough

Here's a walkthrough of implemented features:

<img src='https://github.com/shamli1997/Serverless-Data-Analysis-Platform/blob/main/private-vpc-1.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

## How It Works

1. **Data Access**:
   - **Public RDS**: The Lambda function accesses the public RDS database directly.
   - **Private RDS**: The Lambda function accesses the private RDS database within the VPC.

2. **Data Analysis**:
   - Lambda functions are triggered to perform analysis on the data retrieved from both RDS databases.

3. **Storing Results**:
   - The results of the analysis are stored in an S3 bucket.

## Getting Started

### Setting Up RDS Instances

1. **Create Public RDS**:
   - Set `Publicly Accessible` to `Yes`.
   - Configure security groups and settings.

2. **Create Private RDS**:
   - Set `Publicly Accessible` to `No`.
   - Place the RDS instance in a private subnet within the VPC.

### Configuring Lambda Functions

1. **Create Lambda Functions**:
   - Configure Lambda functions to connect to both public and private RDS databases.
   - Ensure Lambda functions have the necessary permissions and VPC access.

2. **Data Analysis Logic**:
   - Implement data analysis logic within the Lambda functions.

### Storing Results in S3

1. **Create an S3 Bucket**:
   - Set up an S3 bucket to store the results of the data analysis.

2. **Configure Lambda Output**:
   - Ensure Lambda functions store their results in the specified S3 bucket.

## Conclusion

This project demonstrates the integration of serverless computing with traditional relational databases in a secure and efficient manner. By leveraging AWS Lambda, RDS, S3, and VPC configurations, you can build a scalable data analysis platform that meets various data processing needs.

