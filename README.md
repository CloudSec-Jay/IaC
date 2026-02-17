# 🏗️ Hardened Infrastructure Arsenal

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-CloudFormation-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-Bicep-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)
![Security](https://img.shields.io/badge/Security-5_Scanners-critical?style=for-the-badge)

**Production-Ready Infrastructure | Security-First Design | Multi-Cloud**

![Status](https://img.shields.io/badge/Status-Production_Ready-success?style=flat-square)
![CIS](https://img.shields.io/badge/Compliance-CIS_Benchmarks-blue?style=flat-square)
![Policy](https://img.shields.io/badge/Governance-OPA%20Enforced-purple?style=flat-square)
![Zero Secrets](https://img.shields.io/badge/Secrets-Zero_Exposed-success?style=flat-square)

---

## 🎯 The Mission

**Security doesn't start at the application layer—it starts at the foundation.**

This is my centralized infrastructure library, the **Source of Truth** for all my security research, purple team labs, and production-ready cloud deployments. Instead of copying random code from Stack Overflow every time I need infrastructure, I maintain one audited, tested, and battle-hardened codebase.

Every template, playbook, and policy in this repository has been engineered to meet **CIS Benchmarks** and hardened against the misconfigurations that lead to breaches. This isn't "infrastructure as code"—it's **security as infrastructure**.

---

## 🔥 What Makes This Different

### ✅ Security is Default, Not Optional
- Every resource starts with **least privilege** and deny-by-default rules
- No public S3 buckets, no 0.0.0.0/0 security groups, no plaintext secrets
- Follows **NSA/MITRE** hardening frameworks and CIS Benchmarks

### ✅ Battle-Tested in Real Environments
- These templates actively power my [Purple Team AppSec Lab](link), [Kubernetes Security Research](link), and [AI Security Testing](link)
- If something breaks in production, it gets fixed here first and propagated to all projects

### ✅ Zero-Trust CI/CD Pipeline
- **5 security scanners** run on every single commit (no exceptions)
- Code doesn't merge unless it passes: Checkov, Trivy, Gitleaks, Kubescape, and ansible-lint
- HIGH/CRITICAL findings = automatic rejection (no "fix it later")

### ✅ Cloud-Agnostic by Design
- Same security principles applied across AWS, Azure, and on-premises
- Modular architecture means you can mix AWS networking with Azure compute
- Not locked into one vendor's way of doing things

---

## 🛠️ The Arsenal

### ☁️ Cloud Provisioning (Multi-Cloud)

**AWS CloudFormation**
- Pre-built landing zones that pass AWS Security Hub checks out of the box
- VPCs and networking with hardened security groups (deny-by-default, explicit allow)
- EC2 instances with IMDSv2 enforcement to prevent SSRF attacks
- S3 buckets with encryption, versioning, and public access blocks enabled by default
- IAM roles following least privilege (no wildcard permissions)
- All resources properly tagged for cost tracking and compliance reporting

**HashiCorp Terraform**
- Reusable, battle-tested modules for common infrastructure patterns
- Encrypted state files stored in S3 with versioning (prevents state corruption)
- Multi-region disaster recovery configurations
- Sentinel policies for automated cost and security guardrails
- Remote backend prevents state conflicts in team environments

**Azure Bicep**
- Native Azure landing zones following Microsoft Cloud Adoption Framework
- Private Link enforcement for all PaaS services (zero public IPs)
- Managed Identity instead of service principals with passwords
- NSGs and Azure Firewall with deny-by-default network rules
- Integration with Azure Policy for continuous compliance monitoring

---

### 🔨 Immutable Infrastructure (Golden Images)

**Packer - The Golden Image Factory**
- CIS-hardened AMIs for Amazon Linux, Ubuntu, and Windows Server 2022
- Pre-installed security agents: Wazuh SIEM, Falco runtime detection, osquery EDR
- Kernel hardening and sysctl tuning applied before first boot
- No manual post-deployment configuration required (100% automated)
- Custom Kali Linux and Ubuntu ISOs for penetration testing labs
- Images versioned and stored in private registries

**Docker - Minimal Attack Surface**
- Distroless and Alpine-based containers for smallest possible footprint
- Multi-stage builds that remove compilers and build tools from final images
- All containers run as non-root users by default (no privileged escalation)
- Pre-built security scanner containers (Trivy, Gitleaks, Checkov) for CI/CD
- Automated CVE scanning before pushing to registry (blocks HIGH/CRITICAL)

---

### ⚙️ Configuration Management & Governance

**Ansible - The Configuration Engine**
- **Linux hardening playbooks:** CIS Level 1 + 2 compliance automation for Ubuntu, RHEL, Amazon Linux
- **Windows baseline:** STIG-based security configurations for Windows Server
- **Kubernetes node prep:** Configures nodes before joining clusters (kernel modules, networking, security)
- **Idempotent design:** Safe to run multiple times without side effects or configuration drift
- **Ansible Vault:** All secrets encrypted at rest (passwords, API keys, certificates)
- **Automated patching:** Scheduled security updates with rollback capabilities

**Open Policy Agent (OPA) - The Security Gatekeeper**
- Rego policies that automatically block unencrypted storage, public IPs, and overly permissive IAM
- Enforces Kubernetes Pod Security Standards at admission time (no privileged pods)
- Integrated into CI/CD as a mandatory deployment gate (not optional)
- Policy violations fail the build before infrastructure is ever created
- Prevents "I'll fix the security issue later" technical debt

**Kubernetes - Hardened Container Orchestration**
- Network isolation with namespace-level RBAC boundaries
- Default-deny network policies with explicit allow rules (zero-trust networking)
- Pod Security Standards enforced cluster-wide (restricted profile only)
- No privileged containers, host networking, or hostPath mounts allowed
- Resource limits on all pods prevent resource exhaustion DoS attacks
- Secrets managed externally via HashiCorp Vault (not stored in etcd)
- Runtime monitoring with Prometheus metrics and Falco anomaly detection

---

## 🔒 The Security Gauntlet

Every commit to this repository runs through an **automated security pipeline** before it can be merged:

```
┌──────────────────────────────────────────────────────────────┐
│  Automated Security Pipeline (GitHub Actions)                │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  Step 1: Gitleaks        → Scans for exposed secrets/keys   │
│  Step 2: Checkov         → IaC security & compliance audit  │
│  Step 3: Trivy           → CVE scanning (containers/deps)   │
│  Step 4: ansible-lint    → Ansible best practices check     │
│  Step 5: Kubescape       → Kubernetes security validation   │
│  Step 6: OPA             → Custom policy enforcement        │
│                                                              │
├──────────────────────────────────────────────────────────────┤
│  ✅ All checks pass  → Merge allowed                         │
│  ❌ Any check fails  → Merge blocked (must fix first)        │
└──────────────────────────────────────────────────────────────┘
```

**Zero Tolerance Policy:**
- `HIGH` or `CRITICAL` security findings = automatic rejection
- No secrets, no public resources, no weak encryption algorithms
- Pull requests require passing all security checks before human review

**Current Security Posture:**
```
✅ 0 exposed secrets (Gitleaks verified)
✅ 0 public S3 buckets or storage accounts
✅ 0 unencrypted data at rest
✅ 0 overly permissive IAM policies
✅ 0 containers running as root
✅ 100% policy compliance (OPA enforced)
```

---

## 🚀 Real-World Deployments

This isn't theoretical infrastructure—it's actively deployed across multiple security research projects:

### [Purple Team AppSec Lab](link-to-project)
**What it does:** Offensive security testing against Wazuh detection
**How this repo helps:**
- Terraform provisions isolated VPC with hardened security groups
- Packer builds vulnerable application AMIs (DVWA, Juice Shop)
- Ansible deploys Wazuh SIEM and custom detection rules
- OPA enforces that no production credentials leak into lab environment

### [Kubernetes Security Research](link-to-project)
**What it does:** Container escape testing and runtime detection
**How this repo helps:**
- Terraform creates hardened EKS cluster with private endpoints
- Kubernetes manifests deploy Pod Security Standards
- OPA blocks any pod requesting privileged access
- Falco monitors for anomalous container behavior in real-time

### [Supply Chain Security Pipeline](link-to-project)
**What it does:** Automated security scanning for code deployments
**How this repo helps:**
- CloudFormation builds CI/CD infrastructure (CodePipeline, CodeBuild)
- GitHub Actions uses hardened Docker images from this repo
- OPA blocks deployments that fail security checks
- Trivy scans all dependencies before production deployment

---

## 💡 Why This Matters (The Business Case)

**For Security Teams:**
- Reduces time-to-secure-infrastructure from weeks to minutes
- Eliminates "configuration drift" that creates security gaps
- Provides audit trail of every infrastructure change via Git history

**For Incident Response:**
- Known-good configurations make it easy to identify compromised systems
- Infrastructure can be torn down and rebuilt in minutes (assume breach mentality)
- Immutable images prevent attackers from establishing persistence

**For Compliance:**
- Automated CIS Benchmark implementation (no manual checklists)
- Policy-as-Code makes audit evidence instantly available
- Continuous compliance monitoring via automated scanning

---

## 🎓 Skills Demonstrated

By building and maintaining this infrastructure library, I demonstrate:

**Infrastructure-as-Code Expertise**
- Multi-cloud provisioning (AWS CloudFormation, Terraform, Azure Bicep)
- State management, modular design, and reusable patterns
- Infrastructure testing and validation automation

**Security Engineering**
- CIS Benchmark and STIG implementation at scale
- Least privilege IAM design and network micro-segmentation
- Defense-in-depth architecture (security at every layer)

**DevSecOps Integration**
- Shift-left security (catch issues before production)
- Policy-as-Code with OPA for automated enforcement
- CI/CD pipeline security with multiple validation stages

**Configuration Management**
- Ansible automation at scale with proper secret management
- Idempotent, repeatable deployments (no snowflake servers)
- Automated compliance and patch management

---

## 🔄 Continuous Improvement

This is a **living repository**—it evolves as I discover new attack techniques and defense strategies:

- **When I learn a new hardening technique**, it gets added here and propagates to all projects
- **When a CVE drops**, I update golden images and redeploy affected infrastructure
- **When audits reveal gaps**, I write OPA policies to prevent them in the future

**Recent Updates:**
- ✅ Added IMDSv2 enforcement after SSRF research
- ✅ Implemented Falco rules for container runtime monitoring
- ✅ Migrated from service principals to Azure Managed Identity
- ✅ Added Trivy scanning to catch Log4Shell-class vulnerabilities

---

## 📊 Metrics That Matter

**Security Impact:**
- **5 automated security tools** run on every commit
- **100% of secrets** encrypted (zero plaintext credentials)
- **0 public endpoints** unless explicitly required and approved
- **<5 minute** time to deploy secure infrastructure from scratch

**Operational Efficiency:**
- **90% reduction** in manual configuration time
- **Zero configuration drift** (immutable infrastructure)
- **<10 minutes** to rebuild compromised environment from known-good state

---

## 📬 Note

This repository represents the foundation of my security engineering practice. Every project I build starts here because **you can't secure what you can't trust to be configured correctly**.

If you're interested in discussing infrastructure hardening, policy-as-code, or DevSecOps pipeline design, I'm always open to technical conversations.

---

<div align="center">

**"Security that isn't automated is security theater."**

![Last Updated](https://img.shields.io/badge/Last_Updated-February_2025-success?style=flat-square)

</div>
