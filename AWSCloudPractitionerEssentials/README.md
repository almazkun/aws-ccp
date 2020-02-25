# AWSCloudPractitionerEssentials

## Intro to AWS Cloud Concepts 
**SCALABILITY (resize resources as needed), AGILITY (learn from and quickly adapt to change), RELIABILITY, SECURITY**

- **Move from Data Centers to Cloud** -- Before cloud computing, enterprises designed and built own data centers.  If under-planned, risked poor performance; if over-planned (planned for worst case scenario), risked wasting money.  Cloud computing enables customers to access data centers and all of its resources via the internet.  This elastic infrastructure of cloud computing frees enterprises from the constraints of fixed and finite IT infrastructure, and minimizes the uncertainty of forecasting hardware needs.  **ELASTICITY** allows enterprises to easily scale computing resources up (as workload grows) or down (when certain resources are no longer required).  Specifically, the AWS tools Autoscaling and Elastic Load Balancing enable applications to automatically scale up or down based on demand.  With the cloud, customers/enterprises easily adapt their consumption of services to meet seasonal requirements / accommodate new strategic directions.

- **DATA SECURITY** -- Security of customer’s data a top priority for Amazon.

- **HIGH AVAILABILITY AND DEPENDABILITY** -- AWS facilities exist all over the world; as a result, AWS customers can literally have a global reach with just a moment’s notice (lower latency).

- **AGILITY** -- Change management & testing & reliability & capacity planning become more agile and efficient with the AWS cloud.  Since cloud computing learns from and quickly adapts to change, it reduces risks (and reduces the cost of change). 

- **AWS PRIORITIZES RELIABLE COVERAGE** -- The AWS Cloud has a high fault tolerance (system can remain operational even if some components of the system fail).

- **SERVICES** -- Cloud computing offers on-demand delivery of IT resources and applications via the internet; compute and storage resources available whenever needed.  AWS offers compute, storage, databases, analytics, networking, mobile, developer and management tools, IOT, security, and enterprise applications.  AWS’ predeveloped services can be quickly assembled as building blocks – automate software delivery and create security and compliance guardrails.

<br>

## AWS Management Interfaces
**MANAGEMENT CONSOLE, CLI, SDKs (CLI & SDKs are tools to customize AWS features)**

Three ways to use AWS:
- **AWS Management Console (GUI that supports majority of AWS)**
  - Available as a mobile app to access features on the go
  - Resource groups are specific to identities (each user in account can customize)

- **Command Line Interface (CLI – open source tool built for interacting with AWS services)**
  - Programming language agnostic
  - Flexibility to create scripts (automate and repeat deployment of AWS resources)
  - Environments: (i) Linux, (ii) Windows, (iii) Remotely (run commands on Amazon EC2 instances, SSH, or with Amazon EC2 Systems Manager)

- **Software Development Kits (SDKs – offers flexibility to create applications and use AWS in existing applications)**
  - Incorporate the connectivity and functionality of the wider range of AWS Cloud Services into your code
  - Enable applications built on AWS to manage your infrastructure’s code
  - Access AWS using a variety of popular programming languages (JavaScript, Python (boto), PHP, .NET, Ruby, Go, Node.js, C++, Java)

<br>

## AWS Core Services
**EC2, EBS, S3, Global Infrastructure, VPC, Security Groups**

### Elastic Compute Cloud (EC2)
 - **Elastic** – if properly configured, automatically scale servers required by an application according to current demands on that application
 - **Compute** – compute or server resources that are being presented (servers = instances, in AWS lexicon)
 - **Cloud** – cloud-hosted compute resources

Amazon EC2 Instances are (i) pay as you go, (ii) offer a broad selection of hardware and software, and (iii) have global hosting.

**Build and Configure an EC2 Instance** 
 - Login to AWS Console
 - Choose a hosting region
 - Launch EC2 Wizard
 - Select software platform for the instance (choose Amazon Machine Image (AMI))
 - Select hardware capabilities (choose Instance Type)
 - Configure instance Network – default is virtual private cloud (VPC); default auto-assign settings give user a default DHCP address.
 - Add Storage
 - Add Tags – assign the Key Pairs that allow user to connect to instance after it has been launched.
 - Configure Security Group – the set of firewall rules that control the traffic for the instance.
 - Review and Launch
 - Once instance launched, locate public DNS and public IP address; use this DNS info to access EC2 instance via Putty.
<br>

### Elastic Block Store (EBS)
EBS is a storage unit for EC2 instances
 - **Disaster Recovery** – Can backup EBS volume using **snapshots** – AWS allows user to recreate a new volume from a snapshot at any time (like versioning).
 - **Reliability** – EBS volumes designed to be durable and available (data in a volume automatically replicated across multiple servers running in the availability zone).
 - **Security** – Can have encrypted EBS volumes at no additional cost.

**Create, Attach, and Format an EBS Volume to an EC2 Instance**
 - In AWS Console, create EBS volume in same availability zone as EC2 instance(s) to which it will be attached
 - Attach EBS volume to desired EC2 instance from AWS Console
 - Access EC2 instance via SSH; use CLI command *lsblk* to view block storage devices attached to this EC2 instance (this will include the EBS volume just attached through the AWS Console)
 - Can use Linux OS to create a file system on this EBS volume
 - Can mount this EBS volume into a folder on Linux machine
 - At any time can unmount EBS volume from folder – then can detach EBS volume from EC2 instance in AWS Console
 - Once detached/available, can attach this EBS volume to another EC2 instance in same availability zone
<br>

### Simple Storage Service (S3)
Store virtually unlimited number of objects – S3 can handle very large objects such as images, videos, or large data files.
Can access data via AWS Console, CLI, SDKs; can also access data in bucket directly, via REST endpoints (these support HTTP or HTTPS access).

S3 is:
 - **Durable** – data redundantly stored in region
 - **Efficient** – designed for seamless scaling (scales for data growth, application use, and high request volume)
 - **Accessible (offers URL-based access)** – content can be fetched directly over the web (can offload serving of content from your application and allow clients to directly fetch data themselves from S3)

In S3:
 - **Buckets** hold data (retrieved via keys)
 - When creating bucket, name must be DNS-compliant
 - Can add data to bucket via AWS Console (drag and drop) or via AWS CLI.  From AWS Console, can change properties and permissions on a per-object-basis.
 - When retrieving data, can add bucket data to a local folder on an EC2 instance
<br>

### Global Infrastructure
**AWS Global Infrastructure comprised of Regions, Availability Zones, and Edge Locations**
 - **Regions** – geographic areas that host two or more Availability Zones.  Regions are completely separate entities from one another.  Resources in one Region are not automatically replicated to other Regions.  In practice, select a Region that helps minimize latency, lower cost, and adhere to regulatory requirements.
 - **Availability Zones** – collection of data centers in a specific Region.  With reliability in mind, Availability Zones are isolated to protect one Zone from failures in other Zones (if one Zone goes down, the other Zones can handle requests).
 - **Edge Locations** – enable quicker content delivery.  Edge Locations host a Content Delivery Network (CDN) called Amazon Cloud Front.  Requests for content are automatically routed to nearest Edge Location (which is typically located in highly-populated areas) so that the content is delivered faster to the end users.
<br>

### Virtual Private Cloud (VPC)
VPC is the **Networking** AWS service that will meet your networking requirements.

**VPC:**
 - Is a private, virtual network in AWS Cloud (uses same concepts as on-premise networking)
 - Allows complete control of network configuration (ability to isolate and expose resources inside VPC)
 - Offers several layers of security controls (ability to allow and deny specific internet and internal traffic)
 - Is a space into which other AWS services deploy (e.g Amazon EC2 deployed into Amazon VPC and instance protected by structure of network – services inherit security built into network)

**VPC Features:**
 - VPC defines an IP-address space (that is divided into subnets)
 - VPCs are Region-based
 - Each AWS account can create multiple VPCs (that can be used to segregate environments)
 - *IP-address spaces*, *subnets*, and *routing tables* allow you to control what you expose to internet and what you isolate within Amazon VPC.
 - Route tables control traffic between subnets and the internet.  Subnets generally classified as public (direct access to internet) or private (no direct access to internet)
 - *Internet Gateway* needed to make subnets public.
<br>

### Security Groups
Act as built-in firewalls.  Control accessibility to instances.

Control network accessibility to your instances by creating security group rules.
 - HTTP: Port 80
 - HTTPS: Port 443
 - SSH: Port 22

Can create and configure security groups from AWS Console.  Default security group rule denies all inbound traffic and allows all outbound traffic.

<br>

## AWS Integrated Services

### Application Load Balancer
(i) Launch Application Load Balancer (ii) Configure routing (iii) Register targets (iv) Verify routing

**Application load balancer useful when page that is visible at page location (.html) is port-dependent.  Load balancer listens on different ports each with an associated routing rule.  Can route to more than one container from same load balancer.**

Adds unique features and enhancements to classic load balancer:

Added Features:
 - Path and host-based routing (Path-based routing allows creation of rules to route to target groups based on URL in request.  Host-based routing enables ability to have multiple domains supported by same load balancer and route requests to target groups based on domain requested)
 - Dynamic ports
 - Deletion protection and request tracing
 - Native IPv6 support in a VPC
 - AWS Web Application Firewall (WAF) integration

Enhanced Features:
 - Additional Supported Request Protocols (HTTP, HTTPS, HTTP/2, and WebSockets)
 - Enhanced Cloud Watch Metrics (additional load balance metrics and Target Group metric dimension)
 - Enhanced Access Logs (ability to see connection details for WebSocket connections)
 - More Health Checks (insight into target and application health at more granular level)

Application Load Balancer allows you to route different requests to the same instance, but differ the path based on the port.

If you have different containers listening on various ports, you can set up routing rules to distribute traffic to only the desired backend application.

<br>

### Auto Scaling
**Auto Scaling adjusts EC2 instance quantity based on current demands on application**.  It has two main aspects:
 - Automate EC2 resource provisioning.
 - Ensure enough EC2 resources to meet fluctuating performance requirements.

**Scaling Policies** define WHEN to adjust capacity of group.

Amazon Cloud Watch monitors performance of application and can help guide your Auto Scaling condition definitions.  **The conditions you create/specify, define thresholds to trigger adding or removing instances** (e.g., CPU utilization over 80%).

Auto Scaling powerful in environment with fluctuating performance requirements (**allows you to maintain performance while minimizing cost**).  Condition-based policies make your auto-scaling dynamic and able to meet fluctuating requirements.

<br>

### Route 53
Managed service to easily get users to your web content.  Can use Route 53 to purchase a domain.  **Route 53 translates human-readable domain names into the IP-address of an EC2 instance** (e.g., example.com translated into 54.85.178.219).  With Route 53, easily register and resolve DNS names.

AWS Edge Locations house the DNS servers; these locations shorten the distance between your DNS-resolution and your customers.
Route 53 is fully-compliant with IPv4 and IPv6.

<br>

### Relational Database Services (RDS)
Addresses challenges of running a standalone database.
**Amazon RDS is a managed service that sets up, operates, and scales a relational database in the cloud.**  Can run database instance using VPC.

**Disaster Recovery** – **Automatic backups of database instance**.  If master database fails, Amazon RDS automatically brings standby database instance in as new master; thanks to synchronous replication, there should be no data loss.

Available DB Engines: MySQL, Amazon Aurora, MS SQLServer, PostgreSQL, MariaDB, Oracle (a subset of these offer **read replica instances**).  Can reduce load on source database by routing read queries from your applications to the read replica instance (when available).  

RDS ideal for web and mobile applications, e-commerce applications, mobile and online games.

<br>

### AWS Lambda
AWS’ event-driven, serverless compute service.  Lets you run code without provisioning or managing services.  Useful for operating serverless websites.

AWS Lambda is a compute service that runs your backend code and responds to events such as object uploads to Amazon S3 buckets, updates to Amazon DynamoDB tables, data in Amazon Kinesis streams, or in-app activity.  **Code triggered automatically when an event occurs.**
Can invoke your code using API calls made using the AWS SDKs.

The code you run (written in Java, Python, etc.) on AWS Lambdas is called a Lambda Function.

Lambda runs your code only when triggered, using only the compute resources needed (only pay for the compute time you use – subsecond metering).  Can use Cloud Watch Events to trigger Lambda Functions.  **Easy to build applications that respond quickly to new information.**

<br>

### Elastic Beanstalk
Quickly deploy and manage applications in the AWS Cloud.  **Allows quick and simple deployment of your web applications; can quickly upload and deploy pre-existing code** (supports Java SE, Python, .NET, etc.).  Can update your application (with a new version) as easily as you deployed it.

Simply upload your code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring (can still access the underlying resources powering your application at any time and take over some (or all) of these infrastructure elements with Elastic Beanstalk’s management capabilities).

**Within minutes, your applications will be ready to use without any infrastructure or resource configuration on your part.**

**Developer Productivity** – Elastic Beanstalk provisions and operates the infrastructure and manages the application stack (platform) for you, so you don’t have to spend the time or develop the expertise.  **Focus on writing code rather than spending time managing and configuring servers, databases, load balancers, firewalls, and networks.** 

<br>

### Simple Notification Service (SNS)
Used when microservices need to talk to each other, or for event-dependent email notifications (like SharePoint alerts – e.g., email notification if item added/deleted from S3 bucket).

SNS can be used to fan out notifications to end users using mobile push, SMS, and email.

Amazon SNS reliably delivers messages to all valid AWS endpoints, such as Amazon SQS queues and AWS Lambda functions.

With Amazon SNS message filtering, subscribing endpoints receive only the messages of interest, instead of all messages published to the topic.

**Security via Topic Policy** – Amazon SNS topic owners can keep sensitive data secure by setting topic policies that restrict who can publish and subscribe to a topic.

<br>

### CloudWatch
**Monitors your AWS resources and the applications you run on AWS in real time.**

Select Features:
- Collect and track metrics (data about the performance of the systems)
- Collect and monitor log files 
- Set alarms on any of your metrics (measure a single metric and perform 1 or more actions – e.g., trigger an auto-scaling event)
- Automatically react to changes

Gain a system-wide visibility into your resource utilization, application performance, as well as operational health.

Metrics loaded into your account for search, graphing, and alarms.

Alarms invoke actions for *sustained* state changes only.

Aware of operational changes as they occur – responds to these operational changes and takes corrective action as necessary.

Can schedule automated actions that self-trigger at certain times.

Logs – monitor and troubleshoot systems and applications using existing log files.  **Can monitor logs from Amazon EC2 instances in real time (and then archive log data – helpful for security compliance).**  Logs can be streamed in real time to data processing solutions like Amazon Kinesis Streams or AWS Lambda.

Can create dashboards with customizable views of the metrics and alarms you wish to monitor.

<br>

### CloudFront
A fast Content Delivery Network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment.

Can cache content in an Edge Location (more than 80 Edge Locations world-wide) that is closer to actual location of users of application – decreases latency.  Distance between where application running (e.g., Singapore) and where users located (e.g., Seattle) not a transfer speed issue with CloudFront.  Leverages AWS Global Infrastructure to lower latency.

With caching, server calls NOT required for every request on webpage.  Content can be served from cache even if server crashes (resilient).

<br>

### CloudFormation

Create and manage your infrastructure and application stack in a controlled and predictable way.  

Provisions and manages stacks of AWS resources based on templates you create to model your AWS infrastructure.

**Template (JSON file) is your blueprint to define configuration of all AWS resources that comprise your infrastructure and application stack.**  Can also select a sample pre-built template for commonly-used architecture.  Templates enable configuration compliance and faster troubleshooting.

Build and rebuild/modify easily with templates (and parameters and conditions) – Easy to replicate infrastructure (e.g., replicate development environment for production and testing).  Can check your template into version control (to track changes).

Permissions control who has ability to process a template through CloudFormation.

<br>


## AWS Architecture

### AWS Well-Architected Framework
5 pillars: (i) security, (ii) reliability, (iii) performance efficiency, (iv) cost-optimization, (v) operational excellence

**(i) Security:**
- identity and access management
- identify potential security threats (e.g. through analyzing logs – logs enable traceability)
- data protection through encryption
- data backup (replication and recovery when needed)
- automate security best practices

**(ii) Reliability:** 
- recover from issues/failures
- anticipate, respond to, and prevent failures
- ability to dynamically acquire / eliminate computing resources to meet demand and mitigate disruptions
- take advantage of automation through monitoring to anticipate and remediate failures before they even occur
- test recovery procedures
- replace one large resource with multiple smaller resources to reduce impact of any single point of failure on overall system

**(iii) Performance Efficiency:**  
- get right tool for right job
- continually innovate solutions through review
- monitor performance to address any issues before customers disrupted (e.g., with CloudWatch)
- consume advanced technologies *as a service* (especially those that can be difficult to implement)
- global reach

**(iv) Cost-Optimization:** 
- continual refinement and improvement of system (optimize over time – can measure, monitor, and improve architecture from data you’ve collected on AWS platform).
- maximize return on investment
- leverage elasticity to match supply with fluctuating demand
- pay only for resources used
- stop/reduce spending on physical data center operations
- use managed services to reduce cost of ownership

**(v) Operational Excellence:**
- manage and automate changes

<br>

### Fault Tolerance and High Availability

- built-in redundancy of an application’s components

**High Availability Service Tools:**
- Elastic Load Balancers – distributes incoming traffic among instances (customizable)
- Elastic IP Addresses – masks failure of an instance or software by allowing users to use the same IP address(es) with replacement resources (can still access applications even if an instance fails)
- Amazon Route 53 – supports geo-location routing to increase availability of customer-facing applications
- Auto Scaling – scale in/out as necessary to meet fluctuations in demand
- CloudWatch – collects and tracks metrics of your AWS infrastructure (often used in conjunction with Auto Scaling to ensure high availability)

**Fault Tolerant Tools:**
- Amazon Simple Queue Service (SQS) – highly-reliable distributed messaging system to help ensure your queue is always available
- Amazon Simple Storage Service (S3) – highly-durable and fault-tolerant redundant data storage (to ensure still have access to all of your information even if there is a failure)
- Amazon Relational Database Service (RDS) – enhance reliability via automated backups, snapshots, multi-Availability-Zone deployments, etc.

<br>

### Web Hosting
- cost-effective, scalable, and on-demand solution
- helps handle usage peaks in a way that is cost-effective (on-demand provisioning where you only pay for what you use)
- provision testing fleets only when you need them

<br>

## Security

### Introduction to AWS Security
AWS Data Center and Network Architecture Security will satisfy requirements of most security-sensitive customers.  Designed to meet compliance requirements.

AWS Shared Responsibility Model: as AWS user, inherit many security controls that AWS operates, which reduces the number of security controls you have to maintain.

Network Security – built-in firewalls, encryption in transit, private/dedicated connections, distributed denial of service (DDoS) mitigation technology

Inventory and Configuration Management

Data Encryption – to help satisfy specific compliance requirements; can have AWS manage encryption keys or can choose to maintain complete control over encryption keys

Access Control and Management – can define and force managed user access policies across AWS services; IAM, MFA, integration and federation with corporate directories, Amazon Cognito, AWS SSO

Monitoring and Logging capabilities

Many industry-leading partner products also available through AWS Marketplace  

<br>

### Shared Responsibility Model
You and AWS work together to secure your entire application.

Physical, Network, and Hypervisor components of your application stack 100% secured by AWS.

Guest OS, Application, and User Data components of your application stack 100% your responsibility to secure.  AWS has ZERO VISIBILITY into these components.

<br>

### Identity and Access Management
User, group, role used for **authentication**.  Policy Docs (which define permissions) used for **authorization.**
With permissions, can permanently prevent/deauthorize certain actions from happening.

Solution for compromised set of credentials scenario – if using Policy Docs attached to users, and not using root level credentials, security manager (who doesn’t know which account got compromised) can remove every policy doc from all users and groups and roles *in a single action*.  As a result, hacker no longer has access.

<br>

### Amazon Inspector
Automated threat/security assessment service (done both before application deployed and while running in a production environment).  After assessment, Amazon Inspector produces a detailed report of potential security issues with prioritized steps for remediation.  Helps identify security issues before they impact your production application.  AWS security researchers regularly update assessment criteria.

<br>

### AWS Shield

**A managed Distributed Denial of Service (DDoS) protection service that safeguards applications running on AWS.**

In a DDoS attack, multiple sources used to attack target – may impact infrastructure and application layers (way site communicates with other sites); disrupts application availability.

Use Web Application Firewalls (WAFs) to prevent application layer attacks (can customize mitigation).

AWS Shield:
- Standard Tier – *always on* network flow monitoring to detect DDoS attacks (protection from most frequently occurring network and transport layer DDoS attacks).
- Advanced Tier – includes 24/7 access to DDoS Response Team, DDoS cost protection (service credits when services scale-up (spike) in response to a DDoS attack), customizable protection (to mitigate sophisticated application layer attacks).

<br>

### Security Compliance

Customers responsible for following compliance laws and regulations.

In some cases, AWS offers functionality, enablers, and legal agreements to support customer compliance.  AWS provides information about their risk and compliance programs so AWS customers can incorporate AWS controls into their governance frameworks.

**By engaging with AWS in the compliance and governance process, customers can design to compliance requirements.**
Customer Compliance Process:
1. Review trusted information and document compliance requirements
2. Design and implement control objectives that meet compliance requirements
3. Identify and document controls owned by outside partners
4. Verify all control objectives are met and all key controls are designed and operating effectively

<br>

## Pricing and Support

### Fundamentals of Pricing
- Only pay for services you consume; no long-term contract; no termination fees
- Pay as you go (as-needed basis)
- Pay less when you reserve (for services like EC2 and RDS)
- Pay even less per unit by using more (aka ‘tiered pricing’ for services like S3 and data transfer out from EC2)
- Pay even less as AWS grows
- Data transfer IN is always free of charge
- Free usage tier for new customers

### Pricing Details
Cost impacted by these three categories: compute capacity, storage, outbound data transfer (aggregated).  Pricing specifics vary depending on AWS product you are using.

### AWS Trusted Advisor
Trusted Advisor is an online resource that rates how optimal your resources are in terms of cost, performance, security, and fault-tolerance and provides recommended actions for improvement when necessary.

### AWS Support Plans
- Proactive Guidance via Technical Account Manager (TAM)
- Best Practices via the Trusted Advisor online resource
- Account Assistance via AWS Support Concierge

Four support plans: Basic, Developer, Business, Enterprise 

<br>

## Sources
- aws.amazon.com websites
- AWS Cloud Practitioner Essentials (Second Edition) online exam prep videos
