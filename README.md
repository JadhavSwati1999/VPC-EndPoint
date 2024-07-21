
# VPC Endpoints


## What is a VPC Endpoint?

A VPC endpoint enables customers to privately connect to supported AWS services and VPC endpoint services powered by AWS Private Link.

### **There are two types of VPC endpoints:**

An ***interface endpoint*** is an elastic network interface (ENI) with a private IP address from the IP address range of the user’s subnet that serves as an entry point for traffic destined for a supported service. It enables you to privately access services by using private IP addresses.

A ***Gateway endpoint*** is a gateway that you specify as a target for a route in your route table for traffic destined for a supported AWS service. Currently supports S3 and DynamoDB services.

# **VPC Endpoints Key points**

- VPC endpoint enables users to privately connect their VPC to supported AWS services.
- VPC Endpoint does not require a public IP address, access over the Internet, a NAT device, a VPN connection, or AWS Direct Connect to communicate with resources in the service.
- Endpoints are virtual devices, that are horizontally scaled, redundant, and highly available VPC components that allow communication between instances in the VPC.
- Access to the resources in other services can be controlled by endpoint policies.
- By default, the Endpoint policy allows full access to the service. Endpoint policies must be written in JSON format.
- Endpoint policy does not override or replace IAM user policies or service-specific policies (such as S3 bucket policies).

## Create a VPC Endpoint

### Step 1: Create VPC Infrastructure

- Login to AWS Console using your login credentials.
- In the search box search for VPC.
- You will be directed to the VPC’s Dashboard.
- Click on Create VPC.
- In VPC settings select VPC only, and give the appropriate name to the VPC.
- Assign a CIDR to the VPC.
- And create the VPC.


- Your created VPC will be shown in the Your VPCs


- ***Create internet gateway***
- Give a name to the IGW.
- Click on Create Internet Gateway.



- Attach the IGW to the VPC that we have created


- ***Create Two Subnets***
- Create a Public subnet.
- Give the subnet a name, select the availability zone, and give CIDR to the subnet.
- Now, create a Private subnet.


- Both the Public and Private subnets are successfully created.


- Create two route table
- One Public Route table and other Private Route table
- Route IGW in the Public route table, and associate public subnet.
- And in the Private route table associate private subnet.



### Step 2: Create a S3 Bucket (AWS Service)

- Create an S3 bucket by clicking on Create bucket.

- While creating the bucket select, General bucket.
- Give the bucket name.


- Click on Create bucket.


- The bucket is created.


### Step 3: Create Endpoint

- Create an endpoint, and give a name tag to the endpoint.
- Select Category, as AWS service.



- Select S3 service.
- And add a route in the private route table.


### Step 4: Create a role for S3

- Create a role for S3.



- Select trusted entity as AWS service.


- Add permissions
- Select the permissions policies for S3 as AmazonS3FullAccess.



- Name, review, and create
- In Role details, give the role name.



### Step 5: Create Instance

- Create instances one in the public subnet and another in the private subnet.
- Select a public instance and in security modify the IAM Role.


- Modify the IAM role and select the role in the IAM role.


- Connect to the Public instance and access the S3 from here.
- aws s3 ls use this command to access the bucket. This is how the endpoint works.


# **VPC Endpoints Limitations**

- VPC endpoints support IPv4 traffic only.
- Endpoints are supported within the same Region only. You cannot create an endpoint between a VPC and a service in a different Region.
- Endpoints cannot transfer an endpoint from one VPC to another, or from one service to another.