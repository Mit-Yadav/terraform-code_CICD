# 🔄 Enterprise Azure Terraform GitOps & CI/CD Pipeline

[![Terraform](https://img.shields.io/badge/Terraform-1.5+-7B42BC.svg?logo=terraform&logoColor=white)](https://www.terraform.io/)
[![Azure](https://img.shields.io/badge/Microsoft_Azure-Cloud-0089D6.svg?logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/)
[![CI/CD](https://img.shields.io/badge/GitHub_Actions-Automated_GitOps-2088FF.svg?logo=github-actions&logoColor=white)](https://github.com/features/actions)
[![Storage](https://img.shields.io/badge/Azure_Blob_Storage-Remote_State-0078D4.svg?logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/services/storage/)

Automated Infrastructure as Code (IaC) deployment pipeline for Microsoft Azure cloud resources, utilizing GitHub Actions workflows for continuous integration, validation, automated planning, and zero-touch delivery.

---

## 🏗️ Architecture & Deployment Flow

`mermaid
flowchart TD
    subgraph VCS ["Version Control & Automation"]
        A[Git Push / Pull Request] --> B[GitHub Actions Pipeline]
        B --> C[Stage 1: Terraform Init & Setup]
        C --> D[Stage 2: Terraform Plan Validation]
        D --> E[Stage 3: Automated Terraform Apply]
    end

    subgraph AzureCloud ["Microsoft Azure Infrastructure"]
        E --> F[Resource Group Management]
        F --> G[Azure Storage Account - LRS/Standard]
        G --> H[Remote Backend & State Store]
    end
`

---

## 📂 Repository Layout

`
terraform-code_CICD/
├── .github/
│   └── workflows/
│       └── terraform-deploy.yml    # Complete multi-stage GitHub Actions CI/CD pipeline
└── terraform-config/
    ├── provider.tf                 # AzureRM provider configuration & version constraints
    ├── variable.tf                 # Reusable input variables
    └── main.tf                     # Azure Resource Group & Storage Account definitions
`

---

## 🛡️ Pipeline Security & Best Practices

- **Zero Clear-Text Credentials**: Azure authentication is performed using encrypted GitHub repository secrets (AZURE_CREDENTIALS).
- **Gated Deployment Stages**: Pipeline divides execution into sequential stages (	erraform-init -> 	erraform-plan -> 	erraform-apply), ensuring that misconfigurations are detected before changes reach the cloud environment.
- **Auditable & Declarative**: Every infrastructure modification is trackable through Git commit history, aligning with GitOps standards.

---
**Maintained by [Mithilesh Yadav](https://github.com/Mit-Yadav)** | Enterprise DevOps & SRE Engineer