# 🌥️ Introduction to Cloud Computing

## Understanding the Cloud

- **What is the Cloud?**
  - A **server** hosted somewhere that clients (web browsers) access via a **network** to visualize websites.
  - Clients and servers communicate using **IP addresses**.
  
- **Analogy**: 
  - Think of sending a letter:
    - **Client**: You (writing the letter)
    - **Network**: Postal system
    - **Server**: Your friend (the recipient)

- **Components of a Server**:
  - **CPU**: Performs computations (like the brain)
  - **RAM**: Fast memory for quick data access
  - **Storage**: For files and structured data (databases)
  - **Networking**: Routers, switches, and DNS servers

- **Challenges with Traditional IT**:
  - Costs: Rent, power, cooling, maintenance.
  - Scaling: Limited by physical space and time to acquire new servers.
  - Disasters: Vulnerability to events like earthquakes or fires.

---

## Cloud Computing Basics ☁️

- **Definition of Cloud Computing**:
  - The **on-demand delivery** of compute power, database storage, applications, and other IT resources.
  - **Pay-as-you-go pricing**: Pay only for what you use, when you use it.

- **Benefits of Cloud Computing**:
  - **Instant Access**: Get resources within seconds.
  - **Flexibility**: Scale up or down as needed.
  - **User-Friendly Interface**: Easy access to servers, storage, and applications.

- **Everyday Examples of Cloud Services**:
  - **Gmail**: Email storage service
  - **Dropbox**: Cloud storage service
  - **Netflix**: Video-on-demand service built on AWS

---

## Types of Cloud Computing 🔍

1. **Infrastructure as a Service (IaaS)**:
   - **Users Manage**:
     - Applications
     - Data
     - Runtime
     - Middleware
     - Operating System
   - **Provider Manages**:
     - Virtualization
     - Servers
     - Storage
     - Networking
   - **Example**: Amazon EC2, Google Cloud, Azure, Rackspace, Digital Ocean, Linode.

2. **Platform as a Service (PaaS)**:
   - **Users Manage**:
     - Applications
     - Data
   - **Provider Manages**:
     - Runtime
     - Middleware
     - Operating System
     - Networking
   - **Example**: AWS Elastic Beanstalk, Heroku, Google App Engine, Windows Azure.

3. **Software as a Service (SaaS)**:
   - **Users Manage Nothing**; everything is handled by the provider.
   - **Examples**: AWS services like Rekognition, Google Apps (Gmail), Dropbox, Zoom.

---

## Pricing Fundamentals and Responsibilities 💰🔒

- **AWS Pricing Model**:
  - **Pay-As-You-Go Model**:
    - **Compute**: Pay for actual compute time used.
    - **Storage**: Pay for the exact amount of data stored in the cloud.
    - **Networking**: Pay only when data leaves the cloud (data entering the cloud is free).

- **Security in the Cloud**:
  - **Customer Responsibilities**:
    - Your data
    - Configuration settings
    - Operating system security
    - Network and firewall configurations
    - Overall security measures implemented within your cloud environment

  - **AWS Responsibilities**:
    - Security of the Cloud:
      - The underlying infrastructure, including hardware and software
      - Internal security measures and controls
      - Ensuring the cloud services are secure and reliable

- **Importance of the Shared Responsibility Model**:
  - **Shared Responsibility**: Understanding the split between your responsibilities and those of AWS is crucial for effective cloud security management.
  - **Exam Relevance**: In the Certified Cloud Practitioner exam, expect questions regarding the delineation of responsibilities under the Shared Responsibility Model.

- **Acceptable Use Policy**:
  - **Agreement**: By using AWS, you agree to adhere to their Acceptable Use Policy.
  - **Prohibited Actions**:
    - Engaging in illegal, harmful, or offensive activities
    - Security violations (e.g., hacking, unauthorized access)
    - Network abuse (e.g., DDoS attacks)
    - Email and messaging abuse (e.g., spamming)

---

## History of the AWS Cloud 📜

- **Launch of AWS**:
  - **2002**: AWS was launched internally at Amazon.com, recognizing the potential to externalize their IT departments.
  - **2004**: Public offering of **SQS** (Simple Queue Service).
  - **2006**: Expansion with the introduction of **S3** (Simple Storage Service) and **EC2** (Elastic Compute Cloud). 

- **Global Reach**:
  - AWS has applications used by companies like **Dropbox**, **Netflix**, **Airbnb**, and even **NASA**.
  - AWS has been recognized as a **leader** in the Magic Quadrant from Gartner for many years.

- **Current Statistics** (as of 2023):
  - Revenue of **$90 billion** and accounts for about **31%** of the market in Q1 2024, with Microsoft in second place at **25%**.
  - Over **1 million active users**.

- **Building on AWS**:
  - AWS enables the creation of sophisticated and scalable applications for diverse industries:
    - **Use Cases**:
      - Transferring enterprise IT
      - Backup and storage
      - Big data analytics
      - Hosting websites
      - Mobile and social application backends
      - Gaming servers

- **Global Infrastructure**:
  - **Regions**: Clusters of data centers named (e.g., US-East-1, EU-West-3) that host AWS services.
  - **Availability Zones**: Each region has multiple availability zones (minimum of three), isolated from disasters and connected via high-bandwidth, low-latency networking.
  - **Points of Presence (Edge Locations)**: Over **400 points of presence** across 90 cities in 40 countries to optimize content delivery.

- **Choosing an AWS Region**:
  - **Factors to Consider**:
    - **Compliance**: Data may need to remain local.
    - **Latency**: Proximity to users can reduce lag.
    - **Service Availability**: Not all regions have all AWS services.
    - **Pricing**: Costs may vary between regions.


## Conclusion 🎉

- Cloud computing offers flexibility, cost-effectiveness, scalability, and agility.
- Understanding the Shared Responsibility Model is essential for cloud security.

---

# 🛡️ IAM (Identity and Access Management)

### Overview
- IAM stands for **Identity and Access Management**.
- It is a **global service** where we create users and assign them to groups.
- When creating an AWS account, a **root account** is automatically created. 
  - This root user should only be used for initial setup and not for regular tasks.
  
### Users and Groups
- Each user represents one person within the organization.
- Users can be grouped for easier management:
  - **Example**: In an organization with six people (Alice, Bob, Charles, David, Edward, Fred):
    - **Developers Group**: Alice, Bob, and Charles.
    - **Operations Group**: David and Edward.
- Groups can only contain users; they cannot contain other groups.
- A user can belong to multiple groups.
- Users not in a group is possible but not a best practice.

### Permissions
- Users or groups are assigned **IAM policies**, which are JSON documents defining allowed actions.
- **Example Policy**:
  - Allows users to:
    - Use the EC2 service and perform describe actions.
    - Use the Elastic Load Balancing service and perform describe actions.
    - Use CloudWatch.
- AWS follows the **principle of least privilege**:
  - Only grant permissions that a user needs.
  - Avoid giving users unrestricted access to prevent high costs or security vulnerabilities.

### IAM Policies
- When a policy is attached to a group (e.g., Developers), all members inherit that policy.
- Users can have **inline policies** attached directly, independent of group memberships.
- **Example**: If Charles and David are in the audit team, they will inherit that policy in addition to their respective group policies.

### Policy Structure
- IAM policy structure consists of:
  - **Version**: Usually `2012-10-17`.
  - **ID**: Optional identifier for the policy.
  - **Statements**: One or more statements.
  
Each statement includes:
- **Sid**: Optional statement identifier.
- **Effect**: Whether the statement allows or denies access (e.g., allow or deny).
- **Principal**: Accounts, users, or roles to which the policy applies.
- **Action**: List of API calls that are allowed or denied.
- **Resource**: List of resources to which the actions apply.
- **Condition**: Optional criteria for when the statement should apply.

---

## Protecting Users and Groups in IAM 🔐

### Defense Mechanisms
1. **Password Policy**
   - A strong password increases security for your accounts.
   - In AWS, you can set up a password policy with various options:
     - **Minimum Password Length**: Define the minimum number of characters.
     - **Character Types**: Require specific character types (uppercase, lowercase, numbers, non-alphanumeric).
     - **User Password Change**: Allow users to change their passwords or require them to change after a certain period (e.g., every 90 days).
     - **Prevent Password Reuse**: Users cannot revert to previous passwords when changing.
   - A password policy helps protect against brute force attacks.

2. **Multi-Factor Authentication (MFA)**
   - MFA adds an additional layer of security beyond just a password.
   - Users should enable MFA, especially for accounts with higher privileges, to prevent unauthorized access.
   - MFA combines something you know (password) with something you own (security device).
   - **Example**: Alice knows her password and has an MFA device generating a token for login.

### Benefits of MFA
- If Alice’s password is stolen, her account remains secure as a hacker would also need her physical MFA device (e.g., a phone) to log in.

### MFA Device Options in AWS
- Familiarize yourself with these options for the exam:
  1. **Virtual MFA Device**: 
     - Use apps like Google Authenticator or Authy.
     - Supports multiple tokens on a single device.
  2. **Universal 2nd Factor (U2F) Security Key**: 
     - A physical device, like a YubiKey by Yubico, allowing multiple users with one key.
  3. **Hardware Key Fob MFA Device**: 
     - Examples include devices from Gemalto, which are third-party providers.
  4. **Government Cloud MFA**: 
     - Special key fob provided by SurePassID for users of AWS GovCloud.

---

## Accessing AWS
There are three main ways to access AWS:

1. **Management Console** (Web Interface)
   - Protected by username, password, and possibly MFA.
   
2. **Command Line Interface (CLI)**  
   - Allows interaction with AWS services through terminal commands.
   - Requires **access keys** (Access Key ID and Secret Access Key) for authentication.
   - Example:
     - `aws s3 cp` to copy files in S3.
   - Access keys are private and should never be shared. Treat your Access Key ID like a username and your Secret Access Key like a password.

3. **Software Development Kit (SDK)**
   - Allows API calls to AWS from within your code.
   - Different SDKs exist for various programming languages (e.g., Python, Java, JavaScript, .NET).
   - Example: The **AWS CLI** itself is built on **Boto**, the AWS SDK for Python.
   
---

### CLI Overview
- The CLI enables direct access to AWS services via public APIs.
- Useful for automating tasks and managing resources through scripting.
- It's open-source and available on GitHub.

### SDK Overview
- The SDK is integrated into your application to manage AWS services programmatically.
- Available for languages like Python, Java, JavaScript, Ruby, and more.
- Specialized SDKs exist for mobile (Android, iOS) and IoT devices.

---

## IAM Roles

IAM Roles allow AWS services to perform actions on your behalf. Just like users, services need permissions, and these are granted through IAM Roles.

#### What are IAM Roles?
- IAM Roles function similarly to users but are designed for AWS services rather than people.
- AWS services (like EC2 instances or Lambda functions) use these roles to get permissions to perform actions on AWS resources.

#### Example: EC2 Instance Roles
- When we launch an **EC2 Instance** (a virtual server), it may need to interact with other AWS services.
- To allow the EC2 instance to perform actions, we assign it an IAM Role.
  - The role gives the EC2 instance the permissions it needs.
  - Example: If the role allows it, the EC2 instance can retrieve information or perform tasks on AWS.
  
#### Common IAM Role Use Cases:
- **EC2 Instance Roles** – Allow EC2 instances to access other AWS services.
- **Lambda Function Roles** – Provide AWS Lambda functions with the necessary permissions.
- **CloudFormation Roles** – Allow CloudFormation to manage AWS resources on your behalf.

---

## IAM Security Tools

IAM offers several security tools to help manage and monitor user credentials and access within your AWS account.

#### 1. IAM Credentials Report
- **Account-level report** that includes all users in your account.
- Provides the status of their credentials (e.g., passwords, access keys).
- Helps you review and monitor credential usage across your AWS account.

#### 2. IAM Access Advisor
- **User-level tool** that shows service permissions granted to a user and when those services were last accessed.
- Useful for applying the **principle of least privilege** by identifying unused permissions and adjusting user access accordingly.

These tools are essential for maintaining security and ensuring users have the appropriate permissions within your AWS account.

---

## Shared Responsibility Model for IAM

The **Shared Responsibility Model** for IAM outlines what AWS is responsible for and what falls under your responsibility when it comes to managing identity and access in the cloud.

#### AWS Responsibilities
- **Infrastructure security:** AWS manages the underlying infrastructure, including physical security and the global network.
- **Service availability:** AWS ensures the availability and security of IAM as a service.
- **Compliance of IAM services:** AWS is responsible for ensuring that IAM services meet industry compliance standards.

#### Customer Responsibilities
- **User, Group, and Role Management:** You are responsible for creating and managing users, groups, roles, and policies in IAM.
- **Policy Management:** Defining, attaching, and managing policies is your responsibility.
- **MFA Enforcement:** You must enable and enforce Multi-Factor Authentication (MFA) on accounts.
- **Access Key Rotation:** Regular rotation of access keys is required to ensure security, and you must manage this.
- **Permissions Management:** Applying the principle of least privilege and ensuring the correct permissions are assigned to users, groups, and roles is your responsibility.
- **Access Monitoring:** Reviewing IAM permissions, auditing access patterns, and revoking unnecessary access is up to you, not AWS.

---

## IAM Best Practices

To ensure proper management and security when using IAM, here are some best practices:

- **Avoid using the root account:** Use your root account only for initial setup. Create individual IAM users for everyday tasks.
- **One user per person:** Ensure that each person using AWS has their own IAM user. Do not share credentials between users.
- **Use groups for permissions:** Assign users to groups and manage permissions at the group level to maintain security and simplify access management.
- **Implement strong password policies:** Create and enforce a strong password policy to secure user access.
- **Enable Multi-Factor Authentication (MFA):** Require MFA for all users, especially for sensitive roles, to protect against unauthorized access.
- **Use IAM roles for AWS services:** When providing access to AWS services, such as EC2 instances, always use IAM roles instead of credentials.
- **Secure access keys:** If you are using AWS programmatically (CLI or SDK), generate access keys and treat them like passwords. Keep them secret and do not share them.
- **Review permissions regularly:** Use the IAM credentials report and IAM Access Advisor to audit permissions and remove unnecessary access.
- **Never share IAM credentials:** Do not share IAM users or access keys. Keep them private to maintain security.


# 💼 AWS EC2 (Elastic Compute Cloud)

### What is Amazon EC2?
- **Amazon EC2 (Elastic Compute Cloud)** is a service that allows you to rent virtual servers, known as **EC2 instances**, on demand. It provides scalable compute power in the cloud and is fundamental for understanding AWS and cloud computing.
- EC2 is part of the **Infrastructure as a Service (IaaS)** model, where you can launch and manage virtual machines with flexible configurations.

---

### Key EC2 Components
1. **EC2 Instances**:  
   - Virtual machines that can run various operating systems such as **Linux**, **Windows**, or even **Mac OS**.
   
2. **EBS (Elastic Block Store)**:  
   - Network-attached storage that can be used for persistent data storage.
   
3. **Elastic Load Balancer (ELB)**:  
   - Distributes incoming traffic across multiple instances for high availability and fault tolerance.
   
4. **Auto Scaling Group (ASG)**:  
   - Automatically adjusts the number of EC2 instances based on the current demand.

---

### EC2 Instance Configuration Options
- When launching an EC2 instance, several configuration options are available:
  1. **Operating System (OS)**: Choose between Linux, Windows, or Mac OS.
  2. **Compute Power**: Select the number of **vCPUs** (virtual CPUs) and **RAM** based on the requirements of your workload.
  3. **Storage Options**:
     - **EBS (Elastic Block Store)** or **EFS (Elastic File System)** for network-attached storage.
     - **Instance Store** for storage directly attached to the physical hardware.
  4. **Networking**: Choose the type of **network card**, set up **firewall rules** with **Security Groups**, and assign a **public IP** if needed.
  5. **EC2 User Data**: Run a **bootstrap script** during the instance's first launch to automate tasks like installing updates, software, or downloading files.

---

### Bootstrapping with EC2 User Data
- **Bootstrapping** refers to running commands or scripts when the instance is launched for the first time.
  - This script is called **EC2 User Data** and is only executed once, allowing you to automate tasks like:
    - Installing software and updates.
    - Configuring system settings.
    - Downloading necessary files.
  - The **EC2 User Data** runs as the **root user**, meaning all commands have administrative privileges.

---

### EC2 Instance Examples
- EC2 provides a wide range of instance types to suit various workloads. These instances vary in terms of CPU, memory, network performance, and storage options. Here are a few examples:
  
  1. **t2.micro**:
     - **vCPU**: 1
     - **Memory**: 1 GB RAM
     - **Storage**: EBS only
     - **Network Performance**: Low to moderate
     - **Free Tier Eligibility**: 750 hours per month

  2. **t2.xlarge**:
     - **vCPU**: 4
     - **Memory**: 16 GB RAM
     - **Network Performance**: Moderate

  3. **c5d.4xlarge**:
     - **vCPU**: 16
     - **Memory**: 32 GB RAM
     - **Storage**: 400 GB NVMe SSD
     - **Network Performance**: Up to 10 Gbps

  4. **r5.16xlarge**:
     - **vCPU**: 64
     - **Memory**: 512 GB RAM
     - **Network Performance**: High

---

### EC2 Pricing and AWS Free Tier
- **t2.micro** is part of the **AWS Free Tier**, allowing you to run an instance for **750 hours per month** without charge, making it ideal for learning and experimentation.
- EC2 instances are charged based on the **instance type**, **usage time**, and **data transfer**. 

---

## EC2 Instance Types

AWS provides a variety of EC2 instance types optimized for different use cases. Here's a quick overview:

### General Purpose
- **Use Case**: Suitable for a wide range of workloads, such as web servers and code repositories.
- **Balance**: Compute, memory, and networking.
- **Examples**: `t2.micro` (Free Tier), `m5.large`.

### Compute Optimized
- **Use Case**: Compute-intensive tasks like batch processing, media transcoding, high-performance computing (HPC), and gaming servers.
- **Examples**: `c5.large`, `c6g.xlarge`.

### Memory Optimized
- **Use Case**: Applications needing fast memory access, such as relational and in-memory databases, real-time processing of big data.
- **Examples**: `r5.large`, `x1.32xlarge`.

### Storage Optimized
- **Use Case**: Workloads with high data throughput needs, like OLTP systems, NoSQL databases, and distributed file systems.
- **Examples**: `i3.large`, `h1.8xlarge`.

### Instance Naming Convention
- Example: `m5.2xlarge`
  - **Class**: `m` (General purpose)
  - **Generation**: `5` (5th gen)
  - **Size**: `2xlarge` (Instance size with more memory and vCPUs)

For a full list of EC2 instances, visit [EC2 Instances Info](https://instances.vantage.sh/).

---

## Security Groups and Ports

### Overview
Security Groups act as firewalls for EC2 instances, controlling inbound and outbound traffic. They are a fundamental part of AWS network security.

- **Allow Rules Only**: Security Groups only contain allow rules, specifying what traffic can enter or leave an EC2 instance.
- **IP or Security Group Reference**: Rules can reference IP addresses or other security groups.

### Inbound and Outbound Rules
- **Inbound Traffic**: Controls what is allowed to enter the EC2 instance (e.g., access from your computer).
- **Outbound Traffic**: Controls what traffic the EC2 instance is allowed to send out (e.g., accessing external websites).

### Security Group Features
- **Region/VPC Specific**: Security Groups are tied to specific regions or VPCs. You must create new security groups when changing regions or VPCs.
- **Shared Across Instances**: One Security Group can be applied to multiple instances, and instances can have multiple security groups.
- **Firewall Outside EC2**: Security Groups operate outside the EC2 instance, meaning blocked traffic won't even reach the instance.

### Good Practice
- **Separate SSH Security Group**: It's a good practice to create a separate security group just for SSH access.

### Common Ports
- **SSH (Secure Shell)**: Port 22, used to log into Linux EC2 instances.
- **FTP (File Transfer Protocol)**: Port 21, for uploading files to a file share.
- **SFTP (Secure FTP)**: Port 22, for secure file transfer using SSH.
- **HTTP**: Port 80, for accessing unsecured websites.
- **HTTPS**: Port 443, for accessing secured websites.
- **RDP (Remote Desktop Protocol)**: Port 3389, for logging into Windows instances.

### Advanced Feature: Security Group References
- **Security Group to Security Group Communication**: You can reference one security group in the inbound rules of another. This allows EC2 instances with specific security groups to communicate directly, without needing to manage IP addresses.

#### Example:
Imagine you have two EC2 instances:
1. **EC2 Instance A** with **Security Group A**.
2. **EC2 Instance B** with **Security Group B**.

To allow **Instance B** to communicate with **Instance A**, you would set an inbound rule on **Security Group A** like this:
- **Type**: Custom TCP Rule
- **Protocol**: TCP
- **Port Range**: 8080 (or any port your application uses)
- **Source**: Security Group B

This allows all EC2 instances with **Security Group B** attached to them to communicate with instances that have **Security Group A** attached, through the specified port (8080 in this case). 

You don't need to worry about the IP addresses of the EC2 instances; the security group reference handles it.

---

## EC2 Instance Purchasing Options

AWS offers several purchasing options for EC2 instances based on workload requirements, cost optimization, and usage predictability. Here are the primary purchasing options:

#### 1. **On-Demand Instances**
- **Description**: On-demand instances allow you to pay for compute capacity by the second, with no long-term commitments or upfront payments.
- **Use Case**: Ideal for short-term, unpredictable workloads.
- **Example**: You are running a web server during a product launch that could last a few hours or days, but you don't want long-term commitments.
  
#### 2. **Reserved Instances**
- **Description**: Reserved instances are designed for long-term workloads where you can commit to using the instance for a one- or three-year term, offering significant discounts.
- **Types**:
  - **Standard Reserved Instances**: Up to 72% discount, specific to instance type and region.
  - **Convertible Reserved Instances**: Up to 66% discount, with the flexibility to change instance family or type.
- **Example**: You are running a database that you know will be active for at least three years. You purchase a reserved instance for the long-term and get up to 72% off the on-demand price.

#### 3. **Savings Plans**
- **Description**: Similar to reserved instances but more flexible. You commit to a specific amount of usage (in dollars) over one or three years, regardless of instance type.
- **Use Case**: Long-term, steady-state workloads with flexible instance types and regions.
- **Example**: You commit to spending $300 per month across any EC2 instances in the **m5 family** within **us-east-1** for the next three years.

#### 4. **Spot Instances**
- **Description**: Spot instances are unused EC2 capacity that AWS offers at up to 90% discount, but they can be interrupted with minimal warning.
- **Use Case**: Best suited for fault-tolerant, flexible workloads that can handle interruptions.
- **Example**: You are running image processing tasks that can stop and resume without issue, so you use spot instances to save 90% on costs.

#### 5. **Dedicated Hosts**
- **Description**: This option gives you a physical server fully dedicated to your usage, allowing full control of instance placements and access to the underlying hardware.
- **Use Case**: Required for companies with regulatory or compliance needs or for using your own licensing (e.g., BYOL - Bring Your Own License).
- **Example**: Your organization has strict compliance requirements and needs visibility into the physical server hosting your instances.

#### 6. **Dedicated Instances**
- **Description**: These instances run on hardware dedicated to a single customer, but you don’t get access to the physical server. It is different from a dedicated host in terms of control and placement.
- **Use Case**: If you need physical isolation for your instances without managing the physical host.
- **Example**: You want hardware that isn’t shared with other AWS customers, but you don’t need full control over the host.

#### 7. **Capacity Reservations**
- **Description**: You reserve capacity in a specific availability zone (AZ) for any duration. This guarantees that the capacity is available whenever needed but does not offer any pricing discounts.
- **Use Case**: Suitable for applications that need guaranteed capacity in a particular region but are uncertain about when it will be used.
- **Example**: You are planning a high-traffic event in the near future and want to ensure enough compute capacity is available in a specific AZ during the event.

---

### Summary Table of Purchasing Options:

| **Option**               | **Cost**                    | **Duration**               | **Discount**       | **Best For**                             |
|--------------------------|-----------------------------|----------------------------|--------------------|------------------------------------------|
| **On-Demand**             | Highest                     | None                        | 0%                 | Short-term, unpredictable workloads      |
| **Reserved Instances**    | Medium (Up to 72% discount)  | 1 or 3 years                | Up to 72%          | Long-term, steady-state workloads        |
| **Savings Plans**         | Medium (Up to 72% discount)  | 1 or 3 years                | Up to 72%          | Long-term, flexible usage                |
| **Spot Instances**        | Lowest                      | Variable (can be interrupted)| Up to 90%          | Fault-tolerant, flexible workloads       |
| **Dedicated Hosts**       | Highest                     | On-demand or reserved       | Up to 70% (reserved)| Regulatory/compliance needs              |
| **Dedicated Instances**   | High                        | On-demand or reserved       | No discounts       | Isolated hardware usage                 |
| **Capacity Reservations** | On-demand rates             | Any duration                | No discounts       | Ensuring available capacity              |


---

## Shared responsibility Model for EC2

| **AWS Responsibilities**                                   | **User Responsibilities**                          |
|------------------------------------------------------------|---------------------------------------------------|
| Physical Data Center Security                              | Security Group Rules Configuration                |
| Infrastructure Maintenance (e.g., hardware)                | Operating System Updates & Patches                |
| Physical Host Isolation                                    | Software Installation & Management                |
| Faulty Hardware Replacement                                | IAM Role Assignment & Permissions                 |
| Compliance with Certifications & Regulations               | Data Security (e.g., encryption, access controls)  |

---

# 📦 EC2 Instance Storage

This section will cover the different storage options for EC2 instances. EC2 storage provides various methods to store and manage data based on use cases. The three main storage types we'll explore are **EBS (Elastic Block Store)**, **EC2 Instance Store**, and **EFS (Elastic File System)**.

## Elastic Block Store (EBS)
EBS Volumes are network drives you can attach to EC2 instances. They persist data even after the instance is terminated, which makes them ideal for long-term storage.

- **Availability Zones**: EBS volumes are bound to specific Availability Zones. For example, an EBS volume created in `us-east-1a` cannot be attached to an EC2 instance in `us-east-1b` unless you create a snapshot and restore it to the new AZ.
- **IOPS (Input/Output Operations per Second)**: When creating an EBS volume, you must provision the capacity and IOPS in advance, depending on your performance needs.
- **Delete on Termination**: This attribute controls whether the EBS volume is deleted when the EC2 instance is terminated. By default, the root volume is deleted, but you can change this behavior.

### Example Use Case:
An EC2 instance in `us-east-1a` has an attached EBS volume. If you stop the instance and start another instance in the same AZ, you can attach the same EBS volume to the new instance and continue where you left off.

### EBS Snapshots:
You can take snapshots (backups) of EBS volumes to create a restore point. Snapshots allow you to copy data across regions or AZs.

- **EBS Snapshot Archive**: Move snapshots to an archive tier for a 75% cost reduction, but note that restoration from the archive takes 24-72 hours.
- **EBS Recycle Bin**: Snapshots can be temporarily stored in a recycle bin before permanent deletion.

---

## EC2 Instance Store
Instance Store is temporary storage attached directly to the physical hardware of your EC2 instance. It offers better I/O performance but does not persist after the instance is stopped or terminated.

- **High Performance**: Useful for caching, scratch data, or temporary content that requires high disk performance.
- **Ephemeral Storage**: Data is lost when the instance stops, so it's not ideal for long-term storage.
- **Backup Responsibility**: You are responsible for backing up and replicating data if needed.

### Example Use Case:
A web application might use EC2 Instance Store to cache frequent reads and writes for faster access. However, the data is not critical, so its loss after termination is acceptable.

---

## Elastic File System (EFS)
EFS is a fully-managed network file system that can be mounted to multiple EC2 instances simultaneously across multiple AZs.

- **Scalability**: Automatically grows and shrinks as you add or remove files.
- **Shared File System**: Ideal for applications needing shared access to files across multiple instances.
- **Cost**: It is more expensive than EBS but charges based on usage, not provisioned capacity.

### Example Use Case:
An application hosted on multiple EC2 instances across `us-east-1a`, `us-east-1b`, and `us-east-1c` can mount the same EFS file system, sharing the same files and making it highly scalable and redundant.

### EFS Storage Classes:
- **EFS Standard**: The default storage class.
- **EFS Infrequent Access (EFS-IA)**: Offers a 92% lower cost for files that are not accessed frequently, with automatic transitions based on lifecycle policies.

---

## Amazon Machine Images (AMIs)

An **Amazon Machine Image (AMI)** represents a pre-configured template that contains the essential information to launch an EC2 instance, including the operating system, software configuration, monitoring tools, and installed applications. AMIs can be either provided by AWS, created by users, or purchased through the AWS Marketplace.

By using an AMI, we can streamline the process of launching new instances, as the required software and configurations are already prepackaged. This leads to faster boot times and configuration, making the process more efficient. AMIs are region-specific but can be copied across regions to leverage the AWS global infrastructure.

AMIs are created from EC2 instances that are first customized to a desired state. Once customized, the instance is stopped to ensure data integrity, and an AMI is created, which also generates associated **EBS snapshots** behind the scenes. These AMIs can then be used to launch other instances with the same configuration in different availability zones or regions.

There are three primary types of AMIs:
- **Public AMIs**: Provided by AWS, like the Amazon Linux 2 AMI.
- **Private AMIs**: Created and maintained by users for internal use.
- **Marketplace AMIs**: Sold by third parties through AWS Marketplace.

Creating AMIs also opens up potential business opportunities, as users can package their software into an AMI and sell it through the AWS Marketplace.

The **EC2 Image Builder** service further automates the process of creating, maintaining, validating, and testing AMIs. It automates the building of EC2 instances (called "Builder EC2 instances") to customize software installations, such as updates to the OS, firewalls, applications, and more. Once the EC2 instance is configured, an AMI is generated automatically.

To ensure quality, **EC2 Image Builder** also validates AMIs by launching test instances to check that the configuration, security, and applications are functioning as expected. If validation passes, the AMI can be distributed across regions, enabling global deployment of applications.

**Key features of EC2 Image Builder**:
- Automates the creation and validation of AMIs.
- Supports scheduled image builds based on criteria like weekly schedules or package updates.
- Free service, only charging for the EC2 instances and storage used during the process.

This seamless automation improves efficiency and helps maintain consistency across deployments.

---

## Shared Responsibility Model for EC2 Storage

| **Component**              | **AWS Responsibility**                                       | **Your Responsibility**                                      |
|----------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| **EBS Volumes**             | Maintaining the underlying infrastructure                    | Managing data, backups, and snapshots                         |
| **EBS Snapshots**           | Ensuring availability of the snapshot service                | Creating and managing snapshots                               |
| **EC2 Instance Store**      | Managing the physical hardware                               | Managing data, backups, and ensuring replication              |
| **EFS**                     | Maintaining availability and durability of the file system   | Managing data, setting lifecycle policies, and access control |

---

# Elastic Load Balancing and Auto Scaling Groups

## Overview
Elastic Load Balancing (ELB) and Auto Scaling Groups (ASGs) are essential components in building scalable and highly available applications on AWS. They work together to distribute incoming application traffic across multiple targets and automatically adjust the number of running instances based on demand.

---

## Elasticity
**Elasticity** refers to the ability of a cloud environment to dynamically provision and de-provision resources as needed, automatically adjusting to varying workloads. This concept is crucial for maintaining performance while optimizing costs.

### Key Points:
- **Dynamic Resource Management**: Resources can be scaled up or down based on current demand without manual intervention.
- **Cost Efficiency**: Organizations only pay for the resources they actually use, avoiding over-provisioning.
- **Real-time Adjustments**: Elasticity allows systems to react to changes in demand, such as spikes in web traffic during a marketing campaign.

---

## Scalability
**Scalability** is the capability of a system to increase its capacity and accommodate a growing amount of work. This can be achieved by adding resources (vertical scaling) or adding more instances (horizontal scaling).

### Types of Scalability:
1. **Vertical Scalability**: Adding more power (CPU, RAM) to an existing machine.
   - **Example**: Upgrading an EC2 instance type to a larger one to handle increased load.

2. **Horizontal Scalability**: Adding more machines or instances to distribute the load.
   - **Example**: Adding more EC2 instances to an Auto Scaling Group during high traffic periods.

### Key Points:
- **Growth Management**: Scalability ensures that applications can handle increased loads without a drop in performance.
- **Future-proofing**: Scalable architecture can accommodate future growth without significant redesign or restructuring.

---

## High Availability
**High Availability (HA)** refers to the design of systems that ensure a higher operational performance and uptime. This involves minimizing downtime and providing continuous access to services.

### Key Strategies for High Availability:
1. **Redundancy**: Using multiple instances across different Availability Zones to eliminate single points of failure.
   - **Example**: Deploying EC2 instances in multiple AZs so that if one AZ fails, the application remains accessible via instances in another AZ.

2. **Load Balancing**: Distributing traffic among several instances, ensuring that no single instance is overwhelmed.
   - **Example**: Using an Elastic Load Balancer to route requests to healthy EC2 instances, automatically redirecting traffic in case of instance failure.

3. **Health Checks**: Regular monitoring of application components to detect and respond to failures.
   - **Example**: ELB performs health checks on EC2 instances and stops routing traffic to unhealthy instances.

4. **Automatic Recovery**: The system automatically detects and replaces failed components.
   - **Example**: Auto Scaling Groups can terminate unhealthy instances and launch new ones without manual intervention.

---

## Agility
**Agility** in cloud computing refers to the ability to rapidly develop, deploy, and scale applications in response to changing business needs. It allows organizations to innovate faster, adapt to market changes, and improve their overall responsiveness.

### Key Points:
- **Faster Deployment**: Cloud services enable quick provisioning of resources, allowing teams to deploy applications in minutes rather than weeks.
- **Iterative Development**: Agile methodologies, combined with cloud technologies, facilitate continuous integration and delivery (CI/CD), promoting frequent updates and enhancements.
- **Responsive to Change**: Organizations can pivot their strategies quickly, scaling resources up or down based on demand or changing business priorities.
  
### Example:
- A startup can launch a new web application within days using AWS services like EC2. As user demand increases, they can quickly scale their infrastructure with Auto Scaling Groups and Elastic Load Balancers to maintain performance.

---

## Elastic Load Balancing

### What is Elastic Load Balancing?
Elastic Load Balancing is a managed service by AWS that automatically distributes incoming application traffic across multiple EC2 instances, containers, or IP addresses. It provides a single point of access for users, effectively balancing the load to enhance application availability and fault tolerance.

### Key Benefits of ELB
1. **Load Distribution**: Balances incoming traffic across multiple EC2 instances, preventing any single instance from becoming a bottleneck.
2. **Health Checks**: Regularly checks the health of instances and automatically stops routing traffic to unhealthy instances.
3. **SSL Termination**: Simplifies management of SSL/TLS certificates, allowing HTTPS traffic.
4. **High Availability**: Can span multiple Availability Zones (AZs), ensuring the application remains available even if one AZ fails.

### Types of Load Balancers
1. **Application Load Balancer (ALB)**:
   - **Use Case**: Designed for HTTP/HTTPS traffic.
   - **Example**: If you have a web application using microservices architecture, the ALB can route requests based on the URL path, directing traffic to different services.

2. **Network Load Balancer (NLB)**:
   - **Use Case**: Handles TCP and UDP traffic at high performance.
   - **Example**: A gaming application needing low latency can use NLB to manage high volumes of incoming traffic while maintaining performance.

3. **Gateway Load Balancer (GWLB)**:
   - **Use Case**: Routes traffic to virtual appliances, like firewalls or intrusion detection systems.
   - **Example**: If your organization has a firewall running on EC2, the GWLB can direct traffic to it for inspection before reaching the application.


### Architecture Example
- A user accesses a web application through the ALB, which routes the request to one of the available EC2 instances. As more users access the application, the ALB continues to distribute the load effectively.

---

## Auto Scaling Groups

### What is an Auto Scaling Group?
Auto Scaling Groups enable automatic scaling of EC2 instances based on demand, ensuring your application runs optimally at all times without overspending on resources.

### Key Benefits of ASGs
1. **Cost Efficiency**: Only pay for the resources you need, scaling in or out based on demand.
2. **Automatic Recovery**: Detects unhealthy instances and replaces them automatically.
3. **Scalability**: Adjusts the number of EC2 instances up or down based on real-time traffic patterns.

### Components of an ASG
- **Minimum Size**: The minimum number of instances to keep running.
- **Desired Capacity**: The target number of instances, which can change based on scaling policies.
- **Maximum Size**: The maximum number of instances the ASG can scale to.

### Scaling Strategies
1. **Manual Scaling**:
   - Example: Manually changing the capacity of the ASG from 1 instance to 2 during peak hours.

2. **Dynamic Scaling**:
   - **Simple Scaling**:  
     - Example: Set a CloudWatch alarm to add two instances when average CPU utilization exceeds 70% for five minutes.
   - **Step Scaling**:  
     - Example: If CPU usage exceeds certain thresholds, add varying numbers of instances based on the level of usage (e.g., add 1 instance at 70%, 2 instances at 80%).

3. **Target Tracking Scaling**:
   - Example: Set a target to maintain average CPU utilization at 40%. The ASG adjusts the number of instances automatically to stay close to this target.

4. **Scheduled Scaling**:
   - Example: Increase the minimum capacity to 10 instances at 5 PM on Fridays in anticipation of high traffic for a sporting event.

5. **Predictive Scaling**:
   - Example: Using machine learning to analyze historical traffic patterns, the ASG provisions additional instances in advance of expected load peaks, such as during holiday sales.

### Architecture Example
- When user traffic increases, the ASG scales out by launching new EC2 instances. The ELB registers these new instances and starts routing traffic to them, ensuring consistent performance during peak times.

---

## Conclusion
By effectively utilizing Elastic Load Balancing and Auto Scaling Groups, along with understanding concepts of elasticity, scalability, high availability, and agility, AWS allows you to build applications that are not only scalable and highly available but also cost-effective. Implementing these services helps maintain performance and reliability while adapting to changing workloads.
