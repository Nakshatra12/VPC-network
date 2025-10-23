# Task 3: Create and Configure a Virtual Private Cloud (VPC) with Subnets

## Objective
The goal of this task is to understand cloud networking by creating a **Virtual Private Cloud (VPC)** in Google Cloud Platform (GCP) with **public and private subnets**, configure **routes and firewall rules**, and verify **internet access** for public resources while keeping private resources isolated.

---

## 1. VPC Overview

- **VPC Name:** my-vpc  
- **CIDR Block:** 10.0.0.0/24  
- **Region:** asia-south1 (Mumbai)  
- **Purpose:** Learn secure cloud networking and subnet segmentation  

### Subnets

| Subnet Name    | CIDR Block   | Type     | Internet Access |
|----------------|------------|---------|----------------|
| public-subnet  | 10.0.1.0/24 | Public  | Enabled ✅ |
| private-subnet | 10.0.2.0/24 | Private | Disabled ❌ |

---

## 2. Setup Steps

### Step 1: Create VPC
- Go to **VPC Network → VPC Networks → Create VPC network**  
- Name: `my-vpc`  
- Subnet creation mode: **Custom**  

### Step 2: Create Subnets
- **Public Subnet:** 10.0.1.0/24, enable external IPs  
- **Private Subnet:** 10.0.2.0/24, no external IP, enable Private Google Access  

### Step 3: Firewall Rules
- Create rule `allow-public-access` to allow TCP ports 22 (SSH), 80 (HTTP), 443 (HTTPS) from `0.0.0.0/0`  
- Ensures public subnet VMs can be accessed from the internet  

---

## 3. Verification

### Public Subnet
1. Launch VM in `public-subnet` with **external IP**  
2. SSH into VM  
3. Test internet access:
```bash
ping google.com
```
4.Expected Outcome: 64 bytes from 142.250.190.14: icmp_seq=1 ttl=118 time=14 ms


### Private Subnet
1. Launch VM in `private-subnet` with **none external IP**  
2. SSH into VM  
3. Test internet access:
```bash
ping google.com
```
4. Expected Outcome> 64 bytes from … ✅ confirms internal connectivity

## 4. Screenshots

1. **VPC Dashboard** – showing VPC and subnets  

2. **Route Table** – showing subnet routes and default route  

3. **Firewall Rules** – showing rules for public access  

4. **Public Subnet VM Ping Result** – confirms internet access  

6. **Private Subnet VM Ping Result** – confirms no internet access  

---

## 5. Outcome / Learning

By completing this task, I learned:

- How to **create a custom VPC** in Google Cloud Platform  
- How to **segment a VPC into public and private subnets**  
- How to **control internet access using routes and firewall rules**  
- How to **verify connectivity** for public and private subnet VMs  
- Understanding of **real-world cloud networking concepts** such as CIDR blocks, routing, and subnet isolation

---

*End of Task 3*
