# 🚀 DevOps Project — AWS Infrastructure

Hands-on project focused on AWS infrastructure, containerization, and configuration automation.

---

## 📋 Projects

### Project 1 — Nginx Container on AWS
Deployment of a containerized application using Docker, published to the internet via **AWS ECR + App Runner**.

**Technologies:** Docker · Nginx · AWS ECR · AWS App Runner

**Key Achievements:**
- Created a Docker image with Nginx.
- Pushed the image to ECR (Elastic Container Registry).
- Public deployment via AWS App Runner with an automatically generated URL.

---

### Project 2 — EC2 with Custom SSH + Docker via Ansible
Creation of an AWS EC2 instance with SSH access configured on port **4444** (disabling port 22) and Docker installation via Ansible Playbook.

**Technologies:** AWS EC2 · Ansible · Docker · Amazon Linux

**Key Achievements:**
- EC2 instance provisioned via AWS CLI.
- Security Group configured to block port 22 and allow only port 4444.
- Docker installed and validated using an Ansible Playbook.

---

## 🛠️ Technologies Used

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat&logo=nginx&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat&logo=ansible&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)

---

## 📁 Repository Structure

```
AWSProject1/
├── Project1-container/
│   └── app/
│       ├── Dockerfile
│       └── index.html
├── Project2-EC2/
│   └── ansible/
│       ├── inventory.ini
│       └── EC2-Docker-install.yml
└── README.md
```

---

## ▶️ How to Reproduce

**Prerequisites:**
- AWS Account with an IAM user configured.
- AWS CLI installed and configured (`aws configure`).
- Docker installed.
- Ansible installed (`pip install ansible`).

### Project 1 — Deploying the Container

```bash
# 1. Create ECR repository
aws ecr create-repository --repository-name my-app --region us-east-1

# 2. Authenticate Docker with ECR
aws ecr get-login-password --region us-east-1 | \
  docker login --username AWS --password-stdin <ECR_URL>

# 3. Build and push
cd Project1-container/app
docker build -t my-app .
docker tag my-app:latest <ECR_URL>:latest
docker push <ECR_URL>:latest
```

### Project 2 — Running Ansible

```bash
# Replace the EC2 IP in inventory.ini
cd Project2-EC2/ansible
ansible-playbook -i inventory.ini EC2-Docker-install.yml
```

---

## 🔐 Security

- .pem files and AWS credentials are never committed (protected by .gitignore).
- SSH access restricted to port *4444* and limited to the administrator's IP.
- Port 22 **blocked** in the Security Group.

---

## 👨‍💻 Author

**Matheus Ximenes**  
Career Transition to DevOps/SRE/Cloud Engineer
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/matheus-ximenes-511b13182/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/Gansblaidx)
