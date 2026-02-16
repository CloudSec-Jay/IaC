🏗️ The Infrastructure Core: Hardened IaC Library

This is my Master Infrastructure Repository. It serves as the centralized "Source of Truth" for secure, production-ready infrastructure components. These templates and playbooks are engineered to be reusable, cloud-agnostic, and pre-hardened for use across all my security projects and research labs.
🎯 Repository Purpose

In a professional DevSecOps environment, security is built into the foundation. This repository provides:

    Standardized Hardening: Every resource meets CIS Benchmarks or NSA/MITRE frameworks
    Rapid Deployment: Modular code designed to spin up secure environments for Purple Teaming, AppSec testing, and AI research in minutes
    Governance-as-Code: Centralized policy enforcement (OPA) that governs all downstream projects

🛠️ The Hardened Toolchain
Cloud Provisioning (Multi-Cloud Library)

    AWS CloudFormation: Core networking templates (VPC, Subnets, IGW) with hardened Security Group defaults
    HashiCorp Terraform: Modular HCL for cross-cloud resource management and state handling
    Azure Bicep: Native Azure landing zones emphasizing Private Links and Managed Identity

Immutable Build Engine

    Packer: The "Golden Image" factory - builds CIS-compliant AMIs and ISOs for lab environments
    Docker: Minimalist container definitions used as the base for all application-level projects

Configuration & Governance

    Ansible: Master configuration engine handling everything from kernel hardening to automated software deployment using Ansible Vault
    Open Policy Agent (OPA): The gatekeeper - Rego policies ensure no project can deploy resources that violate security baselines
    Kubernetes: Hardened manifest library for deploying containerized workloads with high-security isolation

🕵️‍♂️ Automated Security Verification

To maintain the integrity of this core library, every commit undergoes a Security Gauntlet:

    SAST: ansible-lint, tflint
    Infrastructure Audit: Checkov, Kubescape, OPA
    Secret Detection: Gitleaks
    CVE Scanning: Trivy

All security checks must pass before code can be merged to main.
