# 🚀 Amazon EKS Kubernetes Deployment of Nginx Application

## 📖 Project Overview

This task demonstrates how to deploy an Nginx application on **Amazon Elastic Kubernetes Service (EKS)**. Also covers the complete lifecycle of creating an EKS cluster, deploying an application using Kubernetes manifests, exposing it to the internet through an AWS Load Balancer, and accessing it outside the Kubernetes cluster.

Amazon EKS is a fully managed Kubernetes service that simplifies running Kubernetes workloads on AWS without managing the Kubernetes control plane.

---

# 🎯 Objectives

- Create an Amazon EKS Cluster
- Configure AWS CLI, kubectl, and eksctl
- Deploy an Nginx application using Kubernetes
- Expose the application using a LoadBalancer Service
- Access the application from the internet
- Verify Kubernetes resources
---

# 🛠 Technology Stack

| Category | Technology |
|----------|------------|
| Cloud Platform | AWS |
| Kubernetes Service | Amazon EKS |
| Container Runtime | Docker |
| Container Image | Nginx |
| Kubernetes CLI | kubectl |
| Cluster Management | eksctl |
| Cloud CLI | AWS CLI |
| Operating System | Amazon Linux 2023 |

---

# 📂 Project Structure

```
eks-nginx-deployment/
│
├── deployment.yaml
├── service.yaml
└── README.md
```

---

# 🏗 Architecture

```
Developer
      │
      ▼
EC2 Workstation
      │
      ▼
AWS CLI + kubectl + eksctl
      │
      ▼
Amazon EKS Cluster
      │
      ▼
Deployment
      │
      ▼
Pods
      │
      ▼
LoadBalancer Service
      │
      ▼
AWS Elastic Load Balancer
      │
      ▼
Browser
```

---

# Prerequisites

- AWS Account
- IAM User with Administrator Access
- EC2 Instance (Amazon Linux 2023)
- AWS CLI
- kubectl
- eksctl
- Internet Connectivity

---

# Step 1 : Launch AWS EC2 Instance

Created an EC2 instance that will act as the Kubernetes workstation.

### Instance Configuration

- Amazon Linux 2023
- t3.medium Instance
- 25 GB Storage

### Security Group

Allow the following inbound ports:

| Port | Purpose |
|------|----------|
|22|SSH|
|80|HTTP|
|443|HTTPS|

---

# Step 2 : Install Required Tools

Install and configure the following tools on the EC2 instance.

- AWS CLI
- kubectl
- eksctl
- Git

Verified the installation of each tool before proceeding to cluster creation.

<img width="940" height="511" alt="image" src="https://github.com/user-attachments/assets/5640f14f-19c1-4698-b1c7-6f09b6482fe6" />

---

# Step 3 : Configure AWS CLI

Configure AWS CLI using IAM user credentials.

Configuration includes:

- Access Key
- Secret Key
- AWS Region
- Output Format

This allows the EC2 instance to communicate securely with AWS services.

---

# Step 4 : Create Amazon EKS Cluster

Create a managed Kubernetes cluster using **eksctl**.

Cluster Configuration:

- Cluster Name: **nginx-cluster-1**
- Region: **ap-south-2**
- Managed Node Group
- Two Worker Nodes
- Instance Type: **t3.medium**

Cluster creation generally takes between **15 and 20 minutes**.

<img width="940" height="406" alt="image" src="https://github.com/user-attachments/assets/0481df01-f0e6-4448-bf9a-f230aafe91d2" />

<img width="940" height="481" alt="image" src="https://github.com/user-attachments/assets/0552780d-83c4-40c7-940e-bfb033f62ecb" />

---

# Step 5 : Verify Cluster

After cluster creation, verify:

- Worker Nodes
- Kubernetes Cluster Status
- Kubernetes Context

The worker nodes should appear in **Ready** state.

<img width="1837" height="721" alt="image" src="https://github.com/user-attachments/assets/836afb31-e686-406c-817d-3a5156866f13" />

---

# Step 6 : Deploy Nginx Application

Create a Kubernetes Deployment manifest.

Deployment configuration includes:

- Deployment Name
- Replica Count
- Labels
- Container Image
- Container Port

The deployment creates multiple Nginx Pods that are automatically managed by Kubernetes.

<img width="747" height="522" alt="image" src="https://github.com/user-attachments/assets/e75577b8-cbb9-43bd-813d-ad8f91cb4fa5" />

---

# Step 7 : Verify Deployment

Verify the following Kubernetes resources:

- Deployments
- ReplicaSets
- Pods

Ensure all Pods are in **Running** state.

---

# Step 8 : Create Kubernetes Service

Create a Service manifest to expose the application.

Service Configuration:

- Service Type: **LoadBalancer**
- Port: **80**
- Target Port: **80**

AWS automatically provisions an Elastic Load Balancer for external access.

<img width="940" height="501" alt="image" src="https://github.com/user-attachments/assets/b9352335-6dcb-4eb6-899e-1c81758a9f1e" />

<img width="940" height="94" alt="image" src="https://github.com/user-attachments/assets/c2988b78-bcf4-452b-87db-69f761cb2f40" />

---

# Step 9 : Access Application

Once the LoadBalancer is created:

- Obtain the External DNS Name
- Open the DNS URL in a web browser

The **Welcome to nginx!** page confirms successful deployment.

<img width="940" height="266" alt="image" src="https://github.com/user-attachments/assets/c7bbd9a9-084e-443e-ab30-9123bfc3a58a" />

---

# Step 11 : Verify Kubernetes Resources

Validated the following resources:

- Cluster Nodes
- Deployments
- ReplicaSets
- Pods
- Services

This confirms that the application is successfully deployed and managed by Kubernetes.

<img width="1645" height="260" alt="image" src="https://github.com/user-attachments/assets/0059bbba-ea99-4ffb-8be1-265101c1297c" />


---

# Step 12 : AWS Load Balancer

Amazon EKS automatically provisions an AWS Elastic Load Balancer when a Service of type **LoadBalancer** is created.

The Load Balancer distributes incoming traffic across all running Pods.

Advantages:

- Automatic Load Distribution
- High Availability
- External Access
- Health Checks

<img width="1752" height="717" alt="image" src="https://github.com/user-attachments/assets/4559629a-a7e1-4edc-af4e-468cb9a5da06" />

---

# Step 13 : Application Access

Access the deployed application using:

```
http://<LoadBalancer-DNS>
```

The application becomes publicly accessible without exposing individual Pods.

<img width="940" height="266" alt="image" src="https://github.com/user-attachments/assets/693deba9-1366-4fe9-a6c4-519d126cee6a" />

---

# Step 14 : Project Validation

Verified:

- EKS Cluster is Active
- Worker Nodes are Ready
- Deployment is Running
- Pods are Healthy
- Service is Active
- Load Balancer is Created
- Nginx Homepage is Accessible

---

# Kubernetes Resources Used

| Resource | Purpose |
|-----------|----------|
| Deployment | Manages Pods |
| Pods | Run the Nginx Container |
| Service | Exposes the Application |
| LoadBalancer | External Access |
| Nodes | Execute Workloads |

```


**Email:** *(Add your Email Address)*
