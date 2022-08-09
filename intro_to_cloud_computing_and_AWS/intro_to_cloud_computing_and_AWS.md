# The Building Blocks of Cloud Computing

## Client-Server Computing

-   HTTP protocol uses TCP port 80

-   HTTPS uses port 443

-   The Server Message Block protocol uses port 445

    -   SMB was developed my Microsoft

    -   Used to provide shared access to files and printers across nodes
        on a network

-   Simple Mail Transfer Protocol (SMTP) uses port 25

    -   SMTP is used to send emails to an email server

## Storage (Block vs. File vs. Object)

-   **Block**-based storage

    -   It's the same as using a HDD or SDD.

    -   Computer sees the HDD or SDD as a block of storage and can
        create volumes from it.

    -   Volumes are just partitions of the total available block of
        storage.

    -   Disks can be internal or external (attached using a network).

    -   Personal computers use block storage (C and D drives on Windows
        PCs are partitions).

-   **File**-based storage

    -   Computer can connect to the file storage and access files, but
        it can't create storage volumes like block-based storage.

    -   A filesystem is "mounted" to the OS using a network share.

    -   File-based storage can be used by many users.

    -   Examples include enterprise shared folders (like the G drive at
        Trellis Company)

-   **Object**-based storage

    -   Unlike block- and file-based storage, object-based storage
        doesn't use a file hierarchy (there's no organization by folders
        and subfolders and files yada yada yada)

    -   Object storage is massively scalable and cheap.

    -   Objects can be just about anything: videos, text, images, source
        code files, and more.

    -   Uses a REST API to create, read, update, and delete data.

## IP Addressing Primer

-   IPv4 Addresses have a network and host ID

    -   In the IPv4 address 192.168.0.1, the green numbers are the
        network ID, and the blue number is the host ID.

-   A subnet mask defines the network and IDs

-   IP addresses and their subnet masks are often displayed together

    -   192.168.0.1/24 represents the IP address 192.168.0.1 and the
        subnet mask 255.255.255.0

-   Classes of IP addresses

    -   Class A: 10.0.0.0

        -   Total addresses: 16,777,214

    -   Class B: 172.16.0.0

        -   Total addresses: 65,534

    -   Class C: 192.168.0.0

        -   Total addresses: 255

## Virtualization vs Containers

-   Each VM in a virtualized environment needs an operating system,
    which adds resource needs

    -   Operating systems require a lot of disk space, increasing
        overhead

-   Using a container engine, like Docker, you can use a single instance
    of an operating system to run multiple applications, which are in
    separate "containers"

-   Containers are individually packaged units of code, settings, and
    dependencies for running an application.

-   Containers on the same system are isolated from one another.

-   Each time you start up a VM, you have to start up the operating
    system on that VM, which is slow.

-   With containers, the OS is already running when you need to start up
    an application, which means apps can scale out quicker

-   Containers are resource efficient

    -   Apps on containers don't require their own instance of an
        operating system

    -   Apps on containers only require the memory and disk space
        required to perform their function

# Intro to Cloud Computing

## Legacy/Traditional IT

-   Traditionally, corporate IT was run from a privately owned or leased
    datacenter

-   Legacy IT is expensive.

    -   You install every part of your stack on your own.

-   In addition to setting up the system, you have to back it up for
    disaster recovery.

## What is Cloud Computing

-   Cloud services take out the management and set-up costs of email
    servers, file servers, and other types of physical IT
    infrastructure.

-   Cloud services are based on a consumption or subscription-based
    model

-   Service scales as customer demand rises.

-   On-demand or self-service: when a user can consume and
    manage their cloud resources without having to contact someone;
    scaling happens automatically.

-   Broad network access: a customer can use their cloud
    capabilities using standard network protocols and mechanisms. Can
    access using the internet or Wide Area Network (WAN).

-   Resource pooling: The cloud provider combines their
    physical resources and serves multiple customers at once using a
    multi-tenant model.

-   Multi-tenancy: the idea that you can be using the same
    hardware at the same time as your cloud provider's other customers.

-   Rapid elasticity: Cloud resources and capabilities
    expand and shrink automatically based on usage.

-   Measured service: Your cloud consumption is monitored
    and metered, and that data is readily available to you.

## Example Cloud Application Deployment

-   Using a traditional IT model, a standard application deployment on
    private physical hardware can take months.

-   Using a cloud service to deploy an application, you don't have to
    purchase, set-up, or manage your own hardware.

    -   With cloud services, you still have to deploy and run your
        application and data.

## Launching Cloud Services

-   Launching services like storage and compute servers can be done from
    a web GUI or the command line.

-   You can launch services using a software development kit (SDK)

    -   SDKs are prepackaged code files that developers write to run or
        automate cloud services.

## Cloud computing service models

-   Private Cloud: You manage everything---hardware, software, backup,
    management, the whole stack.

-   Infrastructure as a Service: You manage your data, operating system,
    and everything from the virtual server on up (no physical
    infrastructure or hardware management).

-   Platform as a service: You only manage your data and application
    code (no OS, no runtime, no hardware).

-   Software as a Service: You don't manage anything. You just use an
    application.

    -   This type of usage is called a pure consumption model.

# Demystifying Cloud Architecture

## Stateful vs Stateless services

-   Stateless applications

    -   Example: news website

    -   No information is recorded about the app user's session

    -   No customized response

-   Stateful

    -   Example: Netflix

    -   Records user session info

    -   Uses that info to make recommendations, customizations, etc

-   Even though your computer stores cookies, that does not make the app
    stateful

-   In the cloud, you can have a combo of stateless and stateful (such
    as in an eCommerce service)

## Scaling up and scaling out

-   Scaling up: adding more hardware resources (more CPU, more memory)
    to a specific instance or multiple instances

-   Scaling out: adding whole instances (virtual machines or servers)

## Load balancing

-   A load balancer routes traffic from users to different servers

-   If a server fails, the load balancer will redirect that server's
    user traffic to another server

-   Load balancers help maintain service and increase an application's
    resilience.

## Fault Tolerance

-   Fault tolerance: ensuring that your system has redundant components
    built in, like extra network interface cards and hard disks, in case
    a component fails

-   High availability: makes sure that users can connect to your app
    with as little downtime as possible.

-   Availability Zones: isolated datacenters that host your servers

    -   Your app should be distributed across multiple availability
        zones

    -   Auto Scaling: a service that starts new servers or instances
        when one fails.

        -   Auto Scaling can also tell when your resources are being
            used up and can add more instances automatically to maintain
            application availability.

    -   If an availability zone is unreachable for any reason, the load
        balancer and Auto Scaling services will reroute traffic and
        scale up your resources to maintain app availability.

## Loose Coupling

-   Tight coupling should be avoided

    -   Can occur when your data producers are directly linked to your
        data consumers

        -   Example: web tier servers receive data from clients, then
            send that data directly to the app tier servers that process
            said data. If the app tier servers get overwhelmed by the
            amount of data coming in, they can drop data or fail.

-   Loose coupling introduces buffers in a system

    -   In the web server/app server example, a message queue can act as
        a landing zone for data, while the app tier servers process data
        that came in before. The app tier can request data when it's
        ready so it doesn't get overwhelmed, and the web tier can send
        data off without overwhelming the app tier and can be ready to
        receive new data.

-   Can prevent failure and data loss

-   Loose coupling essentially introduces middlemen to the flow of data.

## Monolithic and Microservices Architectures

-   Monolithic app architecture

    -   Many components interacting on one platform

    -   Updates can potentially cause the whole application to fail

    -   Can have many instances running, which can protect against
        failure

        -   Load balancer can reroute traffic in case of failure or
            updates

-   Microservices app architecture

    -   Each app component is separate "microservice"

    -   A microservice is an independently deployable app or unit of
        code

    -   Microservices communicate with each other through buffers or
        APIs to ensure loose coupling

    -   Microservices are built around different business capabilities

        -   In an eCommerce service, the ordering, billing, and web
            store interfaces would all be different microservices

    -   Containers are good for running microservices

-   Many instances of each microservice can run on each host, and
    microservices can be spread across multiple hosts

-   Each microservice can be implemented using different programming
    languages and settings if you use containers

## Event-Driven Architecture

-   In an event-driven architecture, components of an application will
    respond to each other when certain things happen

    -   In an event-driven eCommerce application, an order may trigger
        an order record to be written to a database server to keep an
        order history. That order record being written might then
        trigger an order processing application to look up that order
        record, then write the details of that order to yet another
        database so it can be analyzed for business analytics reasons.

-   "It this, then that" essentially

# AWS Basics

## AWS Overview

-   AWS was internally launched in 2002

-   Launched publicly in 2004 as Amazon SQS

-   Relaunched in 2006 with Simple Storage Service (S3), SQS, and EC2

-   AWS has over 200 services

## AWS Global infrastructure

-   AWS platform runs on the AWS global infrastructure

-   AWS global network

    -   High bandwidth

    -   Low latency

    -   Redundant

    -   Connects every AWS region

## AWS pricing

-   Three fundamental things you're charged for:

    -   Compute: the amount of memory and processing power you use

    -   Storage: the amount of data you're storing

    -   Outbound data transfer: the outbound traffic of data from your
        services

-   Ways to pay for AWS

    -   Pay as you go: You are charged as you use AWS

    -   Reserve: You buy a set amount of resources for a given period

        -   AWS offers a discount for this kind of usage

    -   Use more, pay less: Use so much AWS that your costs actually go
        down because you've reached a different pricing tier

-   Each service has different pricing models

-   Different pricing throughout the world

-   AWS calculator can create an estimate of how much you can expect to
    pay for your workload

## AWS Identity and Access Management (IAM) Overview

-   The root account (the email that you created the AWS account with)
    has the most access and privileges

-   IAM (pronounced eye-yam) accounts should be used for everyday use

-   IAM users are entities in AWS that represent individuals or services

    -   Services use the IAM account credentials

-   IAM policies are documents that specify the privileges and
    permissions that users, groups, and roles have

-   IAM groups are collections of IAM users that have similar policies

## Amazon Virtual Private Cloud

-   Amazon Virtual Private Cloud (VPC) is a virtual space to launch
    resources

-   A VPC is a logically isolated portion of the AWS cloud within a
    region

-   You can have multiple VPCs in a region

-   Subnets can be created within VPCs

-   VPC routers send information between subnets in a VPC

-   You can configure the VPC's route table to send information to the
    correct places within your VPC

-   0.0.0.0/0 is the destination IP address used to send information
    outside of your VPC on the internet or another public network

-   You can launch virtual servers into your VPC subnets

-   Instances on a private subnet cannot access the internet (mostly)

-   Each VPC has a different block of IP addresses

-   Classless Interdomain Routing (CIDR) allows you to take one IP
    address and create separate address blocks (subnets) within it

    -   Each subnet gets a number of IP addresses to use from the total
        CIDR block of addresses

## Security Groups and Network Access Control Lists (NACLs)

-   Security groups are a type of firewall that controls traffic to and
    from instances or virtual servers in a subnet.

-   Security groups are implemented at the instance level and can apply
    to one or many instances/virtual servers.

-   Traffic to and from instances within the same security group and
    subnet will still be seen by the security group

-   Network access control lists (Network ACLs or NACLs) are a type of
    firewall applied at the subnet level

-   NACLs support allow and deny rules, and they process those rules in
    order until they reach an allow or deny rule.

-   Security groups can be applied to instances in any of your public or
    private subnets

-   Security groups support allow rules only, denying all traffic by
    default when created except from within the same security group.

-   Unlike NACLs, security groups evaluate all their rules and then work
    out what to do.

-   Stateful firewalls vs stateless firewalls

    -   Stateful firewalls send their return traffic automatically,
        without any rules

        -   When you connect to a web server, the request goes through
            the firewall first. Once the server gets your request and
            returns what you asked for/sends an acknowledgement, that
            server outbound traffic doesn't get processed by the
            firewall

    -   Stateless firewalls check for an allow rule in both directions
        (inbound and outbound)

    -   AWS **security groups** are **stateful** firewalls.

    -   AWS **network ACLs** are **stateless** firewalls.

## AWS public and private services

-   AWS services are either:

    -   Private (reside in your VPC)

    -   Public (reside in the AWS cloud)

-   Public and private services are accessible from the internet, but
    you control what traffic connects to your private services

-   Private services (like EC2 instances) use an internet gateway to
    access AWS public services (like S3).

-   VPC endpoint: an ability to connect to public services within the
    VPC.

# Amazon Elastic Compute Cloud (EC2)

## Amazon EC2 Overview

-   EC2 serves as the foundation for many other services

-   EC2 instances = virtual servers or virtual machines

-   EC2 hosts = physical hardware managed by Amazon that run the
    virtualization software that creates the EC2 instances.

-   You can run windows or Linux on EC2 instances

-   Three types of IP addresses for EC2 instances

    -   Public IP address

        -   Address is lost when the instance is stopped and started up
            again

        -   Used in public subnets

        -   Free of charge

        -   Associated with a private IP address on the instance

        -   Cannot move between instances

    -   Private IP address

        -   The address is the same even when the instance is stopped
            and started up again

        -   Used in public and private subnets

    -   Elastic IP address

        -   It is a public IP address, but it remains the same when the
            instance is stopped and started up again, like a private IP
            address.

        -   You're charged if you don't use it, because IPv4 addresses
            like this are running out

        -   Is associated with a private IP address on the instance

        -   Can be moved to new instances and Elastic Network Adapters

            -   Maintains the same IP address even if an instance fails

-   Public IP and Elastic IP instances in a public subnet connect
    directly to your VPC's internet gateway to connect to the outside
    world.

-   Private IP instances in a private subnet cannot connect directly to
    the internet. They have to send their traffic to a network address
    translation (NAT) gateway, which then forwards that connection to
    the internet.

## Launching an EC2 instance

1.  Choose an operating system from the Amazon Machine Image (AMI)

2.  Choose an instance type

    a.  T2.micro is low-power, general use, and free

3.  Configure your instance

## Using Access Keys with EC2

-   EC2 instances can connect to other AWS services using an access key,
    but it's not recommended

-   An attacker can see your access key ID and secret access keys if you
    get access to an instance, which is no Bueno

## Using IAM roles with EC2

-   When you give an instance an IAM role, it allows that instance to
    call other AWS services based on the permissions in that IAM role.

-   IAM roles are more secure than using access keys because no actual
    access key info is stored on the instance

## EC2 auto-scaling

-   Auto-scaling creates and deletes instances to meet demand or
    terminate failed instances

-   You can create an auto-scaling group based on a launch template,
    which is a saved EC2 instance configuration

## Target Tracking Scaling Policies

-   When you create an auto-scaling group, you can configure it with a
    target tracking scaling policy that creates and removes instances
    dynamically based on need.

-   You the target you track will usually be CPU usage

## Elastic Load Balancing

-   The elastic load balancer (ELB) routes traffic coming into your VPC

-   As connection requests come in, the ELB sends the connections to
    different instances on subnets throughout the VPC

-   You can set up an ELB to direct traffic for an auto-scaling group.

# AWS Storage Services

## Overview

-   Storage services available

    -   Elastic Block Store (EBS)

        -   Block-based storage

        -   Connect to volumes over network

        -   Can partition mounted volumes

        -   Mounted to your EC2 instance as a drive you can see on your
            system

    -   Elastic File System (EFS)

        -   File-based storage

        -   Mounted to your instance, but cannot be partitioned

        -   Uses NFS protocol

        -   Linux only

        -   Can connect on-premises clients using a VPN

    -   Simple Storage Service (S3)

        -   Object-based storage

        -   Uses HTTP protocol

        -   You access items using a REST API

## Elastic Block Store (EBS) vs Instance Stores

-   EBS storage is attached to your instance using a network.

-   Instance stores are connected to the hardware running the instance.

-   Instance stores offer higher performance, lower latency

-   Instance stores are ephemeral or nonpersistent storage

    -   Useful for temporary data

-   EBS is persistent storage

## EBS Snapshots and AMIs

-   You can create EBS snapshots of volumes you've created and mount
    them to EC2 instances in other availability zones

-   EBS snapshots are stored at the region level, which is why they can
    be used to create volumes in multiple availability zones within that
    region

-   You can use snapshots to create custom AMIs, or gold images

    -   These AMIs have whatever software or data you've added to the
        AMI you were using when you created the snapshot

    -   Good for launching preconfigured instances with all the software
        and settings you want

## Elastic File System (EFS)

-   EFS is AWS's file based storage system

-   Using EFS you can connect multiple instances to the same file
    system, and you can create and see the same data at the same time

-   You can attach instances from multiple availability zones to an EFS
    store

-   You can only use Linux with EFS

-   Uses the NFS protocol

-   You can use EFS with devices outside the VPC (or on-premises devices
    in a corporate setting)

## Simple Storage Service (S3)

-   Object-based storage

-   You create buckets, which are containers for objects, to store your
    data

-   You connect to your bucket over the internet using a URL

-   Object attributes:

    -   Key (or the name of the object)

    -   Version ID

    -   Value (or the actual data)

    -   Metadata

    -   Subresources

    -   Access control information

-   S3 is a key-value storage solution

-   Connect your instances to S3 using the internet gateway

    -   You can also connect using private IP addresses using S3 Gateway
        Endpoint

-   There are various policies for how your data is stored that
    determine how long and where it is stored

# AWS Databases

## Amazon Relational Database Service (RDS) 

-   Relational databases have more rigid schema

    -   Tables have defined rows and columns

-   RDS runs on EC2 instances

-   RDS can support many database engines:

    -   Amazon Aurora

    -   MySQL

    -   MariaDB

    -   Oracle

    -   Microsoft SQL

    -   PostgreSQL

-   RDS is managed, meaning you don't have access to the underlying
    operating system

-   Multi-AZ is a disaster recovery technology that can create a passive
    RDS Standby instance in a different availability zone

    -   The passive standby created by Multi-AZ is updated using
        synchronous replication

    -   Synchronous replication: a server sends data to a standby
        server, and when the standby gets the data, it has to send a
        message back to the sending server that acknowledges the receipt
        of data

-   Multi-AZ can create an RDS Read Replica instance for handling
    increased database queries (aka database read operations)

    -   The RDS Read Replica is updated using asynchronous replication,
        meaning it doesn't have to send an acknowledgement message back
        to the sending server.

    -   RDS Read Replicas are only used for database reads (aka queries)
        and cannot be written to directly by EC2 instances

    -   RDS Read Replicas take some of the query workload off of the
        main RDS server.

## Amazon DynamoDB

-   Fully managed service.

    -   You don't create your own databases; you create tables that you
        manipulate

-   It's a nonrelational database

    -   Flexible, gives you more control over the schema

-   It offers seamless horizontal scaling (because it's managed)

-   Data gets replicated across multiple AZs automatically

-   DynamoDB is made up of

    -   Tables (where data is stored)

    -   Items (rows in the table)

    -   Atrributes (associated info with each item)

-   You can create items with attributes of different types

    -   An item "example" can have an attribute "attr" that is a string
        (like "one two three") or a number (like 123)

# Automation on AWS

## AWS CloudFormation

-   CloudFormation allows you to deploy your infrastructure using code

    -   EC2 instances, S3 buckets, databases, VPCs

-   CloudFormation creates and configures your resources based on a
    template that you can create and edit

-   You define how you want CloudFormation to set up your infrastructure
    using JSON or YAML

-   You can delete stacks from the CloudFormation console

    -   Make sure to remove all objects from S3 buckets before
        attempting to delete an S3 bucket stack

-   Mappings in a CloudFormation JSON or YAML file can create conditions
    for separate configurations

    -   For example: you can set up a different types of EC2 instances
        depending on the regions and availability zones you're deploying
        into.

-   If your connection request hangs and doesn't successfully connect
    when trying to connect to an application created by a CloudFormation
    template, check to see if:

    -   1\. The instances are running and healthy

    -   2\. If the load balancer and the instances have the correct
        security group rules

## AWS Elastic Beanstalk

-   Platform as a Service

-   You can have your application built for you, you just have to
    provide the application code

-   All you have to do is upload a zip file of your code, specify what
    kind of code it is, and elastic beanstalk sets up all the hardware
    for you

    -   Kind of like how Heroku runs my Olive newsletter app

# [DevOps on AWS: Creating a Code Pipeline]{.underline}

## Continuous Integration and Continuous Delivery (CI/CD)

-   Continuous Integration is how developers build and test code

1.  The developer writes some code alongside other developers

2.  The developer pushes the code to a code repo like GitHub or AWS
    CodeCommit

3.  Build servers build and test the developer's code.

4.  The build servers send the results of the build and test to the
    developer

5.  If code changes are needed, the cycle repeats

-   Continuous Delivery has all the same steps as continuous
    integration, but adds automation for deploying the developers'
    updated code to the application at the end.

-   AWS has tools for CI/CD

    -   CodeCommit is their code repo.

    -   CodeBuild is their build server service.

    -   CodeDeploy is their tool to push updated code out to an
        application.

## AWS CodePipeline with Elastic Beanstalk

-   CodePipline automates the process of deploying your code (using
    CodeDeploy) once you've committed it (to CodeCommit)

-   You can use Git to commit and push changes to your remote CodeCommit
    repo from the command line.

-   Elastic Beanstalk creates the environment for your code, and
    CodePipeline updates the code in that environment as you push
    changes to it for continuous integration/continuous delivery.

## AWS CodeStar

-   CodeStar builds out an environment for your code projects using a
    bunch of AWS developer tools

    -   CloudFormation to automate the creation of your server
        environment

    -   CodePipeline to automate the integration and delivery of new
        code

        -   CodeCommit to store your code in a repo

        -   CodeBuild to build your code and get it ready for deployment

        -   CodeDeploy to ship your code out to your application

-   When you create a project in CodeStar, that project will create an
    S3 bucket, a Lambda function, and an API Gateway endpoint

    -   Lambda is a serverless service, meaning you don't start up an
        EC2 instance to run your code

    -   API Gateway creates an API that you can deploy on AWS. It acts
        as the front door of your application to AWS services on the
        back end.

-   When you delete a project in CodeStar, it automatically deletes all
    the other parts of your infrastructure stack using CloudFormation

# DNS Services and Content Delivery

## AWS Route 53 and Routing Policies

-   Route 53 is a domain name system service

    -   Register your domain name

    -   Create a hosted zone

    -   Perform health checks on your EC2 instances

    -   Use Traffic Flow to route incoming server traffic

-   Route 53 DNS Record Types when you try to connect to an app running
    on AWS

    -   Simple: provides the IP address associated with a name

    -   Failover: if the primary server is down, Route 53 sends you to a
        secondary location

    -   Geolocation: Uses your geographic location to route your traffic
        to the closest region

    -   Geoproximity: Routes you to the closest region within a
        geographic area

    -   Latency: Puts you on the route with the lowest latency

    -   Multivalue answer: Returns several IP addresses and functions
        like a simple load balancer

    -   Weighted: uses traffic limits (or "weights") assigned to the
        resources to decide which route to put you on

## AWS CloudFront

-   CloudFront is a content delivery network (CDN)

    -   Allows you to share content around the world with lower latency

-   CloudFront Origin = the original spot where your data or objects are
    stored

    -   Could be an S3 bucket or EC2 instance

-   Your CloudFront data is cached at different edge locations around
    the world

# Containers and Serverless Computing

## Docker Containers on Amazon Elastic Container Service (ECS)

-   ECS tasks are the running instances of Docker containers in your
    availability zones

-   ECS Services are used to maintain a count of your running tasks

-   An ECS Cluster is a logical grouping of tasks

-   Fargate = serverless implementation of ECS

    -   It is managed for you

    -   You can launch ECS with your own EC2 instances instead of
        fargate

## AWS Lambda

-   Lambda is AWS' serverless technology

-   Serverless means you don't manage any EC2 instances or servers

-   You just upload your code to Lambda

-   It's an event driven service, so it runs your code based on an event
    trigger

# Application Integration and Loose Coupling

## Amazon SNS and Amazon SQS

-   Amazon Simple Notification Service (SNS) sends messages from one
    technology to another

    -   You can send notifications from an app to phone via text, an
        email address via an email message, or to other web applications
        and AWS services via different transport protocols.

-   Amazon SQS can send messages to a queue between EC2 instances to
    create loose coupling

-   Mappings help you connect SQS to other services like Lambda and
    CloudWatch to create event-driven architectures   
