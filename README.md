# Serverless Data Analysis Platform

## Overview

This is a cutting-edge serverless data analysis platform. This platform empowers Lambda functions to access and analyze data from both a public RDS database and a private RDS database, with the results elegantly stored in an S3 bucket.

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

## Architecture Diagram

![Serverless Data Analysis Platform Architecture Diagram](images/architecture-diagram.png)

## How It Works

1. **Data Access**:
   - **Public RDS**: The Lambda function accesses the public RDS database directly.
   - **Private RDS**: The Lambda function accesses the private RDS database within the VPC.

2. **Data Analysis**:
   - Lambda functions are triggered to perform analysis on the data retrieved from both RDS databases.

3. **Storing Results**:
   - The results of the analysis are stored in an S3 bucket.

## Accessing RDS with DBeaver

### Public RDS
- **Accessible**: When the public access setting is enabled (`Publicly Accessible` set to `Yes`), the RDS instance can be accessed using DBeaver.
- **Demo**: Demonstration on how to connect to a public RDS instance using DBeaver.

### Private RDS
- **Inaccessible Directly**: When the public access setting is disabled (`Publicly Accessible` set to `No`), the RDS instance cannot be accessed directly using DBeaver.
- **Demo**: Demonstration on accessing a private RDS instance using DBeaver within the VPC.

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
