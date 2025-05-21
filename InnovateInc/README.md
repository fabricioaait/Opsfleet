# Innovate Inc. Cloud Infrastructure Design 🚀

![AWS Architecture](https://img.shields.io/badge/Cloud_Provider-AWS-orange?logo=amazon-aws&style=for-the-badge)
![Kubernetes](https://img.shields.io/badge/Platform-EKS-blue?logo=kubernetes&style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/Database-RDS_PostgreSQL-blue?logo=postgresql&style=for-the-badge)

## Table of Contents 📚
- [Cloud Environment Structure](#cloud-environment-structure-)
- [Network Design](#network-design-)
- [Compute Platform](#compute-platform-)
- [Database](#database-)
- [High-Level Diagram](#high-level-diagram-)
- [Additional Considerations](#additional-considerations-)

---

## Cloud Environment Structure ☁️

### Recommended Cloud Provider: **AWS**
While both AWS and GCP offer excellent managed Kubernetes services (EKS and GKE respectively), AWS is recommended due to:

✔ **Mature enterprise features**  
✔ **Better regional coverage** for global expansion  
✔ **Stronger security** and compliance certifications  
✔ **More predictable cost structure** for growing workloads  

### AWS Account Structure 🏗️

| Account Type          | Purpose                                                                 | Key Features                          |
|-----------------------|-------------------------------------------------------------------------|---------------------------------------|
| **Production**        | Hosts live customer-facing environments                                | Strict security controls, limited access |
| **Staging/Pre-Prod**  | Mirrors production for testing                                         | Final validation before production    |
| **Development**       | Hosts development and testing environments                             | Permissive access for developers     |
| **Shared Services**   | Central IAM, DNS, security services, container registry, monitoring    | Cross-account management             |

**Justification:**  
🔸 Isolation of environments reduces blast radius  
🔸 Clear separation of duties and access controls  
🔸 Simplified cost tracking and chargeback  
🔸 Follows AWS Well-Architected best practices  

---

## Network Design 🌐

### VPC Architecture
```mermaid
graph TD
    A[VPC per Environment] --> B[3 Availability Zones]
    B --> C[Public Subnets]
    B --> D[Private Subnets]
    B --> E[Isolated Subnets]
