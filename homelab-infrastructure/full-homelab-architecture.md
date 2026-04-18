# Homelab Infrastructure (Flagship Project)

## Overview
This project showcases a complete homelab environment simulating a small-scale production IT infrastructure.

It is designed to replicate real-world scenarios involving system administration, service deployment, network configuration, and troubleshooting.

The environment is built around a central server running TrueNAS SCALE, hosting multiple containerized services used for collaboration, automation, and secure remote access.

---
## Skills Demonstrated
- System administration (TrueNAS SCALE)
- Docker container management
- Network configuration and remote access (Tailscale)
- Service deployment and maintenance
- Infrastructure troubleshooting
- Security best practices

---
### Hardware

Server Machine

- CPU: AMD Embedded G-Series SoC GX-420GI (4 cores / 4 threads)

- RAM: 12 GB

- Storage: 128 GB M.2 SSD and 500 GB HDD

- Network: Gigabit Ethernet

This server acts as the primary infrastructure host for all services deployed in the homelab.


---
### Operating Platform

The main infrastructure platform used in this homelab is:

- TrueNAS SCALE

TrueNAS SCALE provides:

- Container management

- storage management

- system monitoring

- snapshot backups

- virtualization capabilities

It serves as the central management platform for the entire environment.


---
## Architecture Overview

The homelab network is connected to the home router and operates within a private network.

Typical structure:

**Internet --> Router --> TrueNAS Server --> Docker Containers**

Some services are accessible remotely through secure networking tools.

Remote access is handled using Tailscale which allows secure access to internal services without exposing ports to the public internet.


---
### Hosted Services

The homelab currently hosts several services used for experimentation and learning.

**Collaboration Platform**

Team communication platform using **Mattermost** with project management via **Focalboard**.

Purpose:

- internal communication

- project management

- team collaboration simulation


---
**DNS Filtering Server**

Network-wide DNS filtering using **Pi-hole**.

Purpose:

- block advertisements

- prevent malicious domains

- improve network privacy


---
**Workflow Automation Server**

Automation workflows powered by **n8n**.

Purpose:

- automate repetitive tasks

- trigger workflows between services

- experiment with automation pipelines


---
**Secure Remote Access**

Secure network access using **Tailscale**.

Purpose:

- connect to homelab remotely

- secure device-to-device networking

- encrypted private access to services


---
**Container Infrastructure**

Applications in this environment are deployed using containerized services managed through **Docker** and orchestrated with **Dockge**. This setup allows services to be deployed, updated, and maintained in an organized and scalable way.

Using containerized applications enables each service to run in an isolated environment while sharing the same host system resources. This approach simplifies deployment and allows multiple services to run reliably on a single server.

Benefits of this container-based infrastructure include:

- service isolation between applications

- simplified deployment and configuration

- easier updates and maintenance

- improved resource efficiency

- better organization of multi-service environments

Docker containers are managed through Dockge, which provides a user-friendly interface for managing container stacks, monitoring running services, and maintaining configuration files for each deployed application.

This setup allows the homelab environment to simulate modern infrastructure practices where containerized services are commonly used for hosting internal tools and applications.


---
**Security Measures**

Security considerations implemented in this environment include:

- private network isolation

- secure remote access via VPN

- limited external exposure of services

- DNS filtering to block malicious domains

These practices help simulate secure infrastructure management practices.

![Network Architecture](https://github.com/vladimirzeth/IT-Portfolio/blob/main/homelab-infrastructure/screenshots/Network%20Architecture.png)

---
## Real-World Relevance

This homelab simulates a small business IT environment where:
- Multiple services are hosted on a single infrastructure
- Remote access is securely managed via VPN
- Internal tools support collaboration and automation
- System failures require troubleshooting and recovery

This setup helps develop practical skills directly applicable to IT Support and System Administration roles.
