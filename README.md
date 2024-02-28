# VPC with Public-Private Subnet in Production

## Overview
This project demonstrates how to create a robust Virtual Private Cloud (VPC) setup suitable for production environments in AWS. The setup includes public and private subnets across two Availability Zones, leveraging features like Auto Scaling Groups, Application Load Balancers, and NAT Gateways to achieve high resiliency and security.

## Key Features
#### Public and private subnets across two Availability Zones for fault tolerance.
#### Load balancer nodes distributing traffic to servers in private subnets.
#### Auto Scaling Group managing server instances for scalability.
#### NAT Gateways providing internet access to servers in private subnets.

## Setup Instructions

### VPC Setup:
#### Create a new VPC with CIDR block 10.0.0.0/16.
#### Create two public subnets with CIDR blocks 10.0.1.0/24 and 10.0.2.0/24 in different Availability Zones.
#### Create two private subnets with CIDR blocks 10.0.3.0/24 and 10.0.4.0/24 in the same Availability Zones as public subnets.

### Internet Gateway (IGW):
#### Attach an IGW to the VPC for internet access in public subnets.

### Route Tables:
#### Create a public route table and associate it with public subnets. Add a route to the IGW.
#### Create a private route table and associate it with private subnets. Add a route to the NAT Gateway.

### NAT Gateway:
#### Create a NAT Gateway in one of the public subnets.
#### Update the route table for private subnets to route internet traffic through the NAT Gateway.

### Security Groups:
#### Create security groups for the instances in public and private subnets, allowing necessary inbound and outbound traffic.

### Auto Scaling Group (ASG)
#### Create an ASG to manage server instances in private subnets. Configure scaling policies based on load metrics.

### Application Load Balancer (ALB):
#### Create an ALB and configure it to distribute traffic to instances in private subnets.

### Deploy Application:
#### Deploy your application on instances in private subnets.

### Monitoring and Logging:
#### Set up CloudWatch alarms for monitoring resource usage and performance.
#### Configure logging for VPC flow logs, ALB access logs, and instance logs for troubleshooting.

### Testing:
#### Test the setup by accessing the application through the ALB. Ensure that traffic is distributed properly and instances scale based on load.


This setup provides a reliable and secure infrastructure for hosting applications in AWS. For detailed implementation steps, refer to the AWS documentation.
