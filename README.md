# Serverless Data Analysis Platform

## Overview

This project revolves around crafting a cutting-edge serverless data analysis platform. This platform empowers Lambda functions to access and analyze data from both a public RDS database and a private RDS database, with the results elegantly stored in an S3 bucket.

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

## Setting Up the Environment

### 1. Setting Up VPC

1. **Create VPC**:
   - Navigate to the VPC Dashboard in the AWS Management Console.
   - Click on "Create VPC".
   - Set a name for your VPC.
   - Choose the IPv4 CIDR block (e.g., `10.0.0.0/16`).
   - Click "Create VPC".

2. **Create Subnets**:
   - Create a public subnet and a private subnet.
   - For the public subnet, choose a CIDR block (e.g., `10.0.1.0/24`).
   - For the private subnet, choose a different CIDR block (e.g., `10.0.2.0/24`).

3. **Create Internet Gateway**:
   - Navigate to "Internet Gateways" in the VPC Dashboard.
   - Click on "Create internet gateway".
   - Attach the internet gateway to your VPC.

4. **Route Table**:
   - Navigate to "Route Tables" in the VPC Dashboard.
   - Create a route table for the public subnet.
   - Edit routes and add a route that directs `0.0.0.0/0` to the Internet Gateway.
   - Associate the public subnet with this route table.

### 2. Setting Up RDS Instances

1. **Create Public RDS Instance**:
   - Navigate to the RDS Dashboard.
   - Click on "Create database".
   - Choose a database engine (e.g., MySQL).
   - Select the "Free tier" template if applicable.
   - In "Connectivity", select the VPC you created.
   - Ensure "Publicly accessible" is set to `Yes`.
   - Choose the public subnet for the database.
   - Set up the database credentials and configurations.
   - Click "Create database".

2. **Create Private RDS Instance**:
   - Follow the same steps as the public RDS instance.
   - Ensure "Publicly accessible" is set to `No`.
   - Choose the private subnet for the database.
   - Click "Create database".

### 3. Setting Up Lambda Functions

1. **Create a Lambda Function**:
   - Navigate to the Lambda Dashboard.
   - Click on "Create function".
   - Choose "Author from scratch".
   - Set the function name and runtime (e.g., Python 3.8).
   - In "Permissions", choose an existing role or create a new role with basic Lambda permissions.

2. **Configure VPC Access for Lambda**:
   - In the Lambda function configuration, go to the "VPC" section.
   - Select the VPC you created.
   - Choose the private subnet.
   - Choose the appropriate security group that allows access to the RDS instance.

3. **Add Environment Variables**:
   - Add environment variables for database connection details (e.g., hostname, username, password).

4. **Deploy Code**:
   - Write and deploy your Lambda function code that connects to the RDS instances, performs data analysis, and stores results in S3.

### 4. Storing Results in S3

1. **Create an S3 Bucket**:
   - Navigate to the S3 Dashboard.
   - Click on "Create bucket".
   - Set a unique name for your bucket.
   - Choose the region.
   - Configure bucket settings as needed.
   - Click "Create bucket".

2. **Configure Lambda to Store Results**:
   - Ensure your Lambda function code includes logic to store analysis results in the specified S3 bucket.

## Conclusion

This project demonstrates the integration of serverless computing with traditional relational databases in a secure and efficient manner. By leveraging AWS Lambda, RDS, S3, and VPC configurations, you can build a scalable data analysis platform that meets various data processing needs.

