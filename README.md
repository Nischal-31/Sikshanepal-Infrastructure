# SikshaNepal Infrastructure

Production infrastructure and deployment configuration for **SikshaNepal**, a Django-based e-learning platform.

## Live Application

The application can be accessed through:

* **https://sikshanepal.com**
* **https://www.sikshanepal.com**

## Architecture

```text
                    Internet
                       │
          ┌────────────┴────────────┐
          │                         │
   sikshanepal.com          www.sikshanepal.com
          │                         │
          └────────────┬────────────┘
                       │
                NGINX Ingress
                       │
                  Kubernetes
                  ┌────┴────┐
                  │         │
              Django     PostgreSQL
              Backend     Database
                  │
                Docker
                  │
                AWS EC2
```

## Tech Stack

* **Cloud:** AWS EC2
* **IaC:** Terraform
* **Configuration:** Ansible
* **Containers:** Docker
* **Orchestration:** Kubernetes
* **Ingress:** NGINX Ingress Controller
* **TLS:** Cert-Manager + Let's Encrypt
* **Database:** PostgreSQL
* **CI/CD:** GitHub Actions
* **OS:** Ubuntu Linux

## Deployment Flow

```text
Terraform
    ↓
AWS EC2
    ↓
Ansible
    ↓
Docker & Kubernetes
    ↓
SikshaNepal Deployment
    ↓
NGINX Ingress
    ↓
Let's Encrypt HTTPS
    ↓
sikshanepal.com
```

## Repository Structure

```text
├── terraform/       # AWS infrastructure
├── ansible/         # Server configuration
├── kubernetes/      # Kubernetes manifests
└── README.md
```

## Deployment

```bash
# Provision AWS infrastructure
cd terraform
terraform init
terraform apply

# Configure the server
cd ../ansible
ansible-playbook playbooks/site.yml

# Deploy to Kubernetes
cd ../kubernetes
kubectl apply -f .
```

## Security

Sensitive files are excluded from version control, including:

* Environment variables
* Kubernetes secrets
* SSH private keys
* Terraform state
* Credentials

## Project

**SikshaNepal** — A centralized e-learning platform built with Django, containerized with Docker, and deployed on AWS using Kubernetes and automated infrastructure tooling.