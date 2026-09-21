<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=28&duration=3000&pause=800&color=EE0000&center=true&vCenter=true&width=700&lines=%F0%9F%9A%80+Ansible+AWS+Automation;%E2%98%81%EF%B8%8F+Infrastructure+as+Code;%E2%9A%99%EF%B8%8F+Ansible+%2B+CloudFormation" alt="Typing banner" />

# 🚀 Ansible AWS Automation

### ⚡ *Automating AWS infrastructure with **Ansible Playbooks** and **CloudFormation Templates***

[![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)](https://www.ansible.com/)
[![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com/)
[![CloudFormation](https://img.shields.io/badge/CloudFormation-FF4F8B?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com/cloudformation/)
[![EC2](https://img.shields.io/badge/EC2-FF9900?style=for-the-badge&logo=amazonec2&logoColor=white)](https://aws.amazon.com/ec2/)
[![S3](https://img.shields.io/badge/S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white)](https://aws.amazon.com/s3/)
[![VPC](https://img.shields.io/badge/VPC-8C4FFF?style=for-the-badge&logo=amazonvpc&logoColor=white)](https://aws.amazon.com/vpc/)
[![YAML](https://img.shields.io/badge/YAML-CB171E?style=for-the-badge&logo=yaml&logoColor=white)](https://yaml.org/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](#-license)

<!-- 🎥 Drop a terminal recording here: asciinema rec → agg demo.cast docs/demo.gif -->
<img src="docs/demo.gif" alt="Playbook run demo" width="720" />

</div>

---

## 📌 Project Overview

> 🧠 This repository demonstrates how to **create, manage, and stop EC2 instances** using Ansible, plus CloudFormation templates for provisioning **EC2, VPC, Security Groups, Subnets, and S3**.

| ✅ | Capability |
|----|-----------|
| 🖥️ | EC2 instance creation using Ansible |
| 🛑 | EC2 instance stop automation |
| 🔐 | AWS authentication using **Ansible Vault** |
| 🔁 | Multiple EC2 provisioning using **loops** |
| 🌐 | AWS **VPC** creation using CloudFormation |
| 🧩 | **Subnet** creation |
| 🔥 | **Security Group** creation |
| 🏗️ | EC2 instance creation **inside a VPC** |
| 🪣 | **S3 bucket** creation |
| 📤 | CloudFormation **Outputs** |
| 📜 | **Infrastructure as Code (IaC)** |

---

## 🛠️ Technologies Used

<div align="center">

| ☁️ Cloud | ⚙️ Automation | 📦 Services |
|---------|--------------|------------|
| 🟧 **AWS** | 🔴 **Ansible** | 🖥️ **AWS EC2** |
| 🖱️ **AWS CLI** | 🔐 **Ansible Vault** | 🪣 **Amazon S3** |
| 🏗️ **CloudFormation** | 📄 **YAML** | 🌐 **Amazon VPC** |
| — | — | 🔥 **Security Groups** |

</div>

---

## 📂 Project Structure

```text
📦 Ansible/
 ┣ 📜 ec2_cteate.yaml     # 🖥️  Create 3 EC2 instances (loop)
 ┣ 📜 ec2_stop.yaml       # 🛑 Stop EC2 instances
 ┣ 📜 ec2_vpc_s3.yaml     # 🏗️  CFN: VPC + Subnet + SG + EC2 + S3
 ┣ 📜 playbook.yaml       # ▶️  Main playbook
 ┣ 📜 sample.yaml         # ☁️  CFN: Basic EC2 + S3
 ┗ 📜 .yaml
```

> ℹ️ **Note:** `ec2_cteate.yaml` is the current filename in this project.

---

# 🔹 Ansible Playbooks

## 1️⃣ EC2 Instance Creation

### 📄 File
```text
ec2_cteate.yaml
```

Creates **3 EC2 instances** using the `amazon.aws.ec2_instance` module:

```text
🟢 Ansible Node1
🟢 Ansible Node2
🟢 Ansible Node3
```

### ⚙️ Configuration

| 🏷️ Setting | ⚙️ Value |
|------------|---------|
| 💿 **AMI ID** | `ami-01a00762f46d584a1` |
| 💻 **Instance Type** | `t3.medium` |
| 🌍 **Region** | `ap-south-1` |
| 🔑 **Key Pair** | `Dhadi` |
| 🌐 **Public IP** | ✅ Enabled |
| 🔐 **Credentials** | `secrets.yaml` (Vault-encrypted) |
| 🔁 **Loop** | Used for multiple instances |

### ▶️ Run
```bash
ansible-playbook ec2_cteate.yaml --vault-password-file vault.pass
```

---

## 2️⃣ Stop EC2 Instances

### 📄 File
```text
ec2_stop.yaml
```

Stops the following instances 🛑

```text
🔴 Ansible Node1
🔴 Ansible Node2
🔴 Ansible Node3
```

### ▶️ Run
```bash
ansible-playbook ec2_stop.yaml --vault-password-file vault.pass
```

---

# 🔐 Ansible Vault

> 🚫 AWS credentials should **never** be stored directly inside the playbook.

### 📄 Secrets file
```text
secrets.yaml
```

```yaml
ec2_access_key: YOUR_ACCESS_KEY
ec2_secret_key: YOUR_SECRET_KEY
```

### 🔒 Encrypt it
```bash
ansible-vault encrypt secrets.yaml
```

### 🗝️ Create a password file
```bash
echo YOUR_VAULT_PASSWORD > vault.pass
```

### ▶️ Run the playbook
```bash
ansible-playbook ec2_cteate.yaml --vault-password-file vault.pass
```

### ⚠️ Security

> ❗ **Never** upload these files if they contain real credentials:

```text
🚫 secrets.yaml
🚫 vault.pass
🚫 *.pem
🚫 *.key
```

✅ Add them to `.gitignore`.

---

# ☁️ CloudFormation Templates

## 3️⃣ Basic EC2 + S3

### 📄 File
```text
sample.yaml
```

Creates:
* 🖥️ EC2 instance
* 🪣 S3 bucket

### 🎛️ Parameters

| 🏷️ Parameter | ⚙️ Default |
|--------------|-----------|
| `AMIId` | `ami-01a00762f46d584a1` |
| `instanceType` | `t3.medium` |
| 🌍 Region | `ap-south-1` |

📤 The template also outputs the **EC2 public IP**.

---

## 4️⃣ VPC + Subnet + Security Group + EC2 + S3

### 📄 File
```text
ec2_vpc_s3.yaml
```

### 🏗️ Architecture

```text
🌐 VPC
 │
 └── 🧩 Subnet
      │
      └── 🖥️ EC2 Instance
           │
           └── 🔥 Security Group

🪣 S3 Bucket
```

### 📦 Resources

| 🧱 Resource | ⚙️ Configuration |
|------------|-----------------|
| 🌐 **VPC** | CIDR `10.0.0.0/16` |
| 🧩 **Subnet** | CIDR `10.0.1.0/24` · AZ `ap-south-1a` |
| 🔥 **Security Group** | SSH · TCP `22` · Source `0.0.0.0/0` |
| 🖥️ **EC2** | `ami-01a00762f46d584a1` · `t3.medium` |
| 🪣 **S3** | Bucket with a specified name |

---

# 📤 CloudFormation Outputs

The `ec2_vpc_s3.yaml` template provides 👇

```text
🆔 VPCId
🖥️ EC2InstanceId
🪣 S3BucketName
```

```yaml
Outputs:

  VPCId:
    Description: VPC ID of the created VPC
    Value: !Ref MyVPC

  EC2InstanceId:
    Description: EC2 Instance ID of the created instance
    Value: !Ref MyInstance

  S3BucketName:
    Description: S3 Bucket Name of the created bucket
    Value: !Ref MyBucket
```

---

# 🚀 CloudFormation Deployment

### ✅ Validate the template
```bash
aws cloudformation validate-template \
  --template-body file://ec2_vpc_s3.yaml
```

### 🏗️ Create the stack
```bash
aws cloudformation create-stack \
  --stack-name ansible-cloudformation-demo \
  --template-body file://ec2_vpc_s3.yaml
```

### 👀 Check the stack
```bash
aws cloudformation describe-stacks \
  --stack-name ansible-cloudformation-demo
```

### 🧹 Delete the stack
```bash
aws cloudformation delete-stack \
  --stack-name ansible-cloudformation-demo
```

---

# 🔄 Ansible Workflow

```text
👨‍💻 Developer
    │
    ▼
📜 Ansible Playbook
    │
    ▼
🔐 Ansible Vault
    │
    ▼
☁️ AWS API
    │
    ▼
🖥️ EC2 Instances
```

---

# 🔄 CloudFormation Workflow

```text
📄 CloudFormation YAML
        │
        ▼
🏗️ CloudFormation Stack
        │
        ├── 🌐 VPC
        ├── 🧩 Subnet
        ├── 🔥 Security Group
        ├── 🖥️ EC2
        └── 🪣 S3
```

---

# 🔒 Security Best Practices

> 🚨 **Do not commit AWS credentials to GitHub.**

### 📄 Recommended `.gitignore`

```gitignore
secrets.yaml
vault.pass
*.pem
*.key
.terraform/
*.tfstate
*.tfstate.*
```

| 🛡️ | Recommendation |
|----|----------------|
| 👤 | Use **IAM roles** in production |
| 🌱 | Use **environment variables** for credentials |
| 🗄️ | Use **AWS Secrets Manager** or similar |
| 🔐 | Avoid hard-coded credentials entirely |

⚠️ Also review security-group rules before deploying. SSH from `0.0.0.0/0` allows connections from **any IPv4 address** and should generally be restricted to trusted IP ranges.

---

# 🎯 Learning Objectives

This project demonstrates practical knowledge of:

| 🧠 | Skill |
|----|-------|
| 📜 | Ansible Playbooks |
| 🧩 | Ansible Modules |
| 🔁 | Ansible Loops |
| 🔐 | Ansible Vault |
| 🖥️ | AWS EC2 automation |
| 🖱️ | AWS CLI |
| 📄 | YAML |
| 🏗️ | Infrastructure as Code |
| ☁️ | AWS CloudFormation |
| 🌐 | VPC networking |
| 🔥 | Security Groups |
| 🪣 | S3 |
| ⚙️ | Cloud automation |

---

# 👨‍💻 Author

<div align="center">

### **Ajay Dhadi**

🟧 **AWS** · 🔧 **DevOps** · ☁️ **Cloud** · 📜 **Infrastructure as Code**

[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/)

</div>

---

## 📄 License

📝 This project is licensed under the **MIT License**.

---

<div align="center">

### ⭐ If this project helped you, give it a star!

Made with ❤️ · ⚙️ **Ansible** · ☁️ **AWS**

</div>
