# GCP Cloud & DevOps – Career Website Deployment

## Project Overview
I deployed a static career guidance website on Google Cloud Platform (GCP) using a custom VPC, subnet, Compute Engine Linux VM, firewall rules, Nginx, and Git/GitHub.

> Current stage: Manual cloud deployment. Docker, CI/CD, and Kubernetes are planned future upgrades.

## Architecture

```text
User
  |
Browser
  | HTTP :80
  v
Internet
  |
External IP
  |
GCP Firewall (TCP 80)
  |
Custom VPC: devops-vpc-demo
  |
Subnet: devops-subnet
10.10.1.0/24
  |
Compute Engine: devops-vm
  |
Debian Linux
  |
Nginx :80
  |
/var/www/html/
  |
Career Website
```

### SSH administration

```text
My Computer -> Internet -> Firewall -> TCP 22 -> devops-vm -> Linux
```

## GCP Resources

| Resource | Configuration | Purpose |
|---|---|---|
| Project | `my-project-tensing123` | Cloud resource container |
| VPC | `devops-vpc-demo` | Network environment |
| Subnet | `devops-subnet` | VM IP range |
| Region | `us-central1` | Subnet region |
| CIDR | `10.10.1.0/24` | Private IP range |
| VM | `devops-vm` | Hosts the website |
| Zone | `us-central1-a` | VM location |
| OS | Debian 12 | Server OS |
| Firewall | TCP 22, TCP 80 | Controls incoming traffic |
| Web server | Nginx | Serves website |
| Source control | Git/GitHub | Stores project code |

## Website

**TechPath / Choose Your Career**

Built with:
- HTML
- CSS
- JavaScript

The site provides career guidance, IT job exploration, resume-related functionality, and learning resources.

## What I Implemented

### 1. Custom VPC
Created `devops-vpc-demo` to provide an isolated network environment.

### 2. Subnet
Created `devops-subnet` with:

```text
10.10.1.0/24
```

### 3. Compute Engine VM
Created `devops-vm` with:
- `e2-micro`
- Debian 12
- `us-central1-a`
- `devops-vpc-demo`
- `devops-subnet`

### 4. Firewall
Allowed:
- **TCP 22** — SSH administration
- **TCP 80** — HTTP website traffic

### 5. SSH

```bash
gcloud compute ssh devops-vm --zone=us-central1-a
```

### 6. Nginx

```bash
sudo apt update
sudo apt install -y nginx
sudo systemctl start nginx
sudo systemctl status nginx
```

Nginx was verified as **active (running)**.

### 7. Local web-server test

```bash
curl localhost:80
```

### 8. Website deployment

The website files were deployed to:

```text
/var/www/html/
```

The website was then accessed through the VM's external IP.

## Request Flow

```text
Browser
  |
HTTP :80
  |
Internet
  |
External IP
  |
Firewall
  |
VPC
  |
Subnet
  |
VM
  |
Nginx :80
  |
/var/www/html/
  |
Website
```

## Why Each Component Is Used
- **VPC:** provides the cloud network.
- **Subnet:** provides an IP address range for resources.
- **CIDR:** defines the subnet IP range.
- **VM:** provides the Linux server.
- **Firewall:** controls allowed network traffic.
- **SSH 22:** lets the administrator access the server.
- **HTTP 80:** lets website visitors reach the web server.
- **Nginx:** receives HTTP requests and serves website files.
- **Git/GitHub:** provides version control and project storage.

## Useful Commands
```bash
# SSH
gcloud compute ssh devops-vm --zone=us-central1-a

# Nginx status
sudo systemctl status nginx

# Start Nginx
sudo systemctl start nginx

# Stop Nginx
sudo systemctl stop nginx

# Restart Nginx
sudo systemctl restart nginx

# Test web server
curl localhost:80

# Check Nginx version
nginx -v
```

## Learning Outcomes

- GCP VPC and subnet creation
- CIDR and private IP addressing
- Compute Engine VM deployment
- Internal and external IP concepts
- Firewall and TCP ports
- SSH administration
- Linux server management
- Nginx installation and configuration
- Website deployment
- Git/GitHub source control
- End-to-end cloud request flow

## Real-World Use Case

A small company can use a similar architecture:

```text
Customers
   |
Internet
   |
Firewall
   |
Cloud VPC
   |
Compute Engine
   |
Nginx
   |
Company Website
```

A production system can later add a load balancer, HTTPS, multiple servers, monitoring, databases, containers, CI/CD, and Kubernetes.

## Future Improvements

### Completed
```text
GCP + VPC + Subnet + Compute Engine
Linux + Firewall + Nginx
Git/GitHub + Website Deployment
```

### Planned
```text
Docker
   |
GitHub Actions / CI-CD
   |
Kubernetes / GKE
```

These technologies will be added after they are actually implemented and tested.

## Project Status

**Completed:** GCP VPC, subnet, VM, Linux, firewall, Nginx, website deployment, Git/GitHub.

**Future:** Docker, CI/CD, Kubernetes, GKE, Infrastructure as Code.

## Author

**Tensing Ch**  
B.Tech – Computer Science Engineering
