### AWS lambda
In **AWS (Amazon Web Services)**, a **Lambda** is a **serverless function** that runs your code automatically in response to events (like file upload to S3, HTTP request via API Gateway) without you managing servers.
In 2 simple lines:
* You just write the code.
* AWS runs it only when needed and scales automatically.

#### 1. ASG (Auto Scaling Group):
It automatically adjusts the number of EC2 instances in your application based on demand (traffic, CPU usage, etc.).
Helps ensure your app has enough servers during high load and saves costs during low load.

#### 2. ALB (Application Load Balancer):
It distributes incoming traffic across multiple targets (EC2 instances, containers) based on rules like URL path or host.
Works at the application layer (HTTP/HTTPS) and helps with high availability and fault tolerance.

* **Public Subnet:** A subnet in a VPC that has a route to the internet via an Internet Gateway. It is used for resources that need direct internet access, such as web servers.
* **Private Subnet:** A subnet in a VPC that does not have a direct route to the internet. It is used for resources that should remain internal, like databases and application servers.

* **NAT Gateway Attachment:** A **NAT Gateway** is deployed in a **public subnet** and allows instances in **private subnets** to access the internet for updates or external communication, **without exposing them directly**.
* It is **attached to the route table** of the private subnet, so all outbound traffic from private instances goes through the NAT Gateway.

**VPC (Virtual Private Cloud):**
An AWS VPC is a **logically isolated network** within AWS where you can launch and manage your resources securely.

**Main Components of a VPC:**
1. **Subnets** – Divide the VPC into public and private sections.
2. **Route Tables** – Control where network traffic is directed.
3. **Internet Gateway (IGW)** – Allows internet access for public subnets.
4. **NAT Gateway/Instance** – Provides internet access to private subnets.
5. **Security Groups (SGs)** – Instance-level firewalls.
6. **Network ACLs (NACLs)** – Subnet-level firewalls.
7. **VPC Peering / VPN / Transit Gateway** – For connecting VPCs or on-premises networks.

### Horizontal Scaling (Scaling Out/In):
Adding or removing more servers/instances to handle load.
Example: Adding 3 more EC2 instances behind a Load Balancer.

### Vertical Scaling (Scaling Up/Down):
Increasing or decreasing the resources (CPU, RAM, Storage) of a single server.
Example: Changing an EC2 instance from t2.micro to m5.large.

👉 In short: Horizontal = more machines, Vertical = bigger machine.

### AWS Secrets Manager 👇
Definition: AWS Secrets Manager is a fully managed service that helps you securely store, manage, and retrieve secrets (like database passwords, API keys, tokens).

# Key Features:
Automatic Rotation → Rotates secrets (like DB passwords) without downtime.
Secure Retrieval → Apps can fetch secrets programmatically using AWS SDK/CLI.
Encryption → Secrets are encrypted using AWS KMS.
Access Control → Uses IAM policies to control who/what can access the secrets.

👉 In short: It replaces hard-coded credentials in apps with a secure, centralized store.

## VPC Peering in AWS 👇

Definition:
VPC Peering is a networking connection between two VPCs that allows them to communicate with each other as if they are in the same network, using private IP addresses.

Key Points:
It is a one-to-one connection (not transitive, meaning VPC A ↔ VPC B doesn’t automatically connect VPC C).
Traffic stays within the AWS private network, not the public internet.
You must update route tables in both VPCs to enable communication.
VPCs can be in the same AWS account or different accounts, even across regions (inter-region VPC peering).

