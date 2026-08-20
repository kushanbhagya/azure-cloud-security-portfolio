# Project 01 — Technical Project Report

## 1. Executive Summary

This project focused on designing and implementing a secure Azure network foundation for a small cloud workload environment.

The architecture uses network segmentation, Network Security Groups, private VM networking, restricted inbound access, and basic monitoring.

The primary security objective was to minimize unnecessary Internet exposure while maintaining a scalable network structure for future workloads.

---

## 2. Problem Statement

Cloud workloads can become vulnerable when unnecessary services are exposed to the public Internet.

A poorly segmented environment can also allow excessive communication between workloads.

This project addresses these risks by implementing:

- Dedicated subnets
- Network Security Groups
- Restricted inbound access
- Private VM networking
- Basic monitoring

---

## 3. Architecture Design

The VNet was designed with three logical workload zones:

### Web

CIDR:

`10.10.1.0/24`

Purpose:

Public-facing workload placement.

### Application

CIDR:

`10.10.2.0/24`

Purpose:

Internal application workloads.

### Management

CIDR:

`10.10.3.0/24`

Purpose:

Administrative and management workloads.

---

## 4. Security Model

The security model follows a defense-in-depth approach.

### Layer 1 — Network Segmentation

Workloads are separated into dedicated subnets.

### Layer 2 — Network Security Groups

Traffic is controlled using subnet-level NSGs.

### Layer 3 — Attack Surface Reduction

The Windows Server VM has no public IP.

### Layer 4 — Monitoring

Azure Monitor provides basic workload monitoring.

---

## 5. Security Decisions

### Decision 1

Do not assign a public IP to the Windows Server VM.

**Reason:**

Reduce direct Internet exposure and eliminate unnecessary public attack surface.

### Decision 2

Allow HTTPS traffic only where required.

**Reason:**

Follow least-privilege principles.

### Decision 3

Do not expose RDP directly to the Internet.

**Reason:**

RDP is an administrative service and should not be unnecessarily exposed.

### Decision 4

Separate management resources into a dedicated subnet.

**Reason:**

Administrative workloads should be logically isolated from application workloads.

---

## 6. Validation

The implemented controls were validated through Azure Portal configuration and resource inspection.

### Network

- VNet configuration verified
- Subnet configuration verified
- NSG associations verified

### Access Control

- HTTPS 443 allow rule verified
- No explicit RDP 3389 allow rule verified
- Default deny behavior reviewed

### VM Security

- Private IP configuration verified
- Public IP absence verified

### Monitoring

- CPU monitoring metric verified
- High CPU alert configured

---

## 7. Limitations

This project intentionally represents a foundational cloud security architecture.

The following enterprise controls were not implemented:

- Azure Bastion
- Azure Firewall
- Private Endpoints
- SIEM integration
- Microsoft Defender for Cloud
- Centralized Log Analytics architecture
- Zero Trust identity controls

These are planned as future improvements or separate projects.

---

## 8. Future Architecture

The next evolution of this environment could introduce:

1. Azure Bastion
2. Azure Firewall
3. Private Endpoints
4. Azure Key Vault
5. Microsoft Defender for Cloud
6. Microsoft Sentinel
7. Centralized logging
8. Azure Policy
9. Identity-based access control
10. Zero Trust architecture

---

## 9. Conclusion

This project established a secure baseline Azure network architecture using practical cloud security principles.

The implementation demonstrates that security can be incorporated directly into network architecture rather than being added after workload deployment.

The architecture is also designed to be extended into more advanced cloud security projects.
