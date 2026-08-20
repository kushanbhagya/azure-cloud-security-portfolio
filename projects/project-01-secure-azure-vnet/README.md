# Project 01 — Secure Azure Virtual Network

> A practical Azure cloud security project focused on network segmentation, access control, secure workload deployment, and basic monitoring.

## 📌 Project Status

![Status](https://img.shields.io/badge/Status-Completed-success)

**Status:** Completed  
**Platform:** Microsoft Azure  
**Focus:** Cloud Security / Network Security  
**Project Type:** Hands-on Home Lab

---

## 📖 Overview

This project demonstrates the design and implementation of a segmented Azure virtual network with security controls for web, application, and management workloads.

The primary objective was to build a secure network foundation following cloud security principles such as:

- Network segmentation
- Least privilege
- Reduced public exposure
- Controlled inbound access
- Secure workload placement
- Basic monitoring

---

## 🎯 Objectives

- Design an Azure Virtual Network using multiple subnets
- Separate web, application, and management workloads
- Implement Network Security Groups
- Allow only required inbound traffic
- Prevent direct Internet-based administrative access
- Deploy a private Windows Server workload
- Configure basic VM monitoring
- Validate the implemented security controls
- Document the architecture and security decisions

---

## 🏗️ Architecture

### High-Level Architecture

```text
                         INTERNET
                            │
                            │ HTTPS : 443
                            ▼
                    ┌─────────────────┐
                    │     nsg-web     │
                    │ Allow TCP 443   │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │    snet-web     │
                    │  10.10.1.0/24   │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │ vm-web-project01│
                    │   Private IP    │
                    │   No Public IP  │
                    └─────────────────┘

              ┌─────────────────────────────────┐
              │       vnet-azcs-project01       │
              │          10.10.0.0/16            │
              │                                 │
              │  snet-app        10.10.2.0/24   │
              │                                 │
              │  snet-management 10.10.3.0/24   │
              │  nsg-management                 │
              └─────────────────────────────────┘
