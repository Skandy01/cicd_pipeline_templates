# Azure DevOps Pipeline Templates  
### Reusable, Modular CI/CD Building Blocks for Application & Infrastructure Delivery

---

## 🎯 Purpose & Scope

This repository provides **Azure DevOps YAML templates** that can be reused across:
- Application CI/CD pipelines
- Infrastructure (Terraform) pipelines
- Security & quality enforcement workflows

The focus is on **modularity, parameterization, and reusability**, not one-off pipelines.

---

## 🧩 What This Repo Demonstrates

✅ Pipeline-as-Code best practices  
✅ Modular design (steps → jobs → stages → pipelines)  
✅ Parameter-driven templates for flexibility  
✅ Separation of concerns (build, scan, deploy)  
✅ Platform-style CI/CD thinking  
✅ Enterprise reusability across teams  

> This repo is designed to be **consumed**, not modified.

---

## 🗂️ Repository Structure

azure-devops-pipeline-templates-enterprise
│
├── templates/
│ ├── steps/ # Small reusable building blocks
│ │ ├── install-node.yml
│ │ ├── install-dotnet.yml
│ │ └── verify-tools.yml
│ │
│ ├── jobs/ # Composed jobs using steps
│ │ ├── build-react.yml
│ │ ├── build-dotnet.yml
│ │ └── terraform-plan-job.yml
│ │
│ ├── stages/ # Full pipeline stages
│ │ ├── ci-stage.yml
│ │ ├── security-stage.yml
│ │ └── deploy-stage.yml
│ │
│ └── pipelines/ # Reference pipeline compositions
│ ├── app-ci.yml
│ └── infra-ci.yml
│
├── examples/ # How real projects consume these templates
│ ├── react-app/
│ ├── dotnet-app/
│ └── terraform-infra/
│
├── docs/
│ ├── usage-guide.md
│ ├── template-catalog.md
│ └── versioning.md
│
├── CHANGELOG.md
└── README.md


---

## 🧱 Template Design Philosophy

### 1️⃣ Steps → Jobs → Stages
Templates are layered intentionally:

- **Steps** → atomic actions (install tools, run commands)
- **Jobs** → logical units of work (build, scan, plan)
- **Stages** → pipeline flow (CI, security, deploy)

This mirrors how **enterprise pipelines are designed and maintained**.

---

### 2️⃣ Parameter-Driven Reuse
Every template is designed to be reusable through parameters:
- Runtime versions (Node, .NET, Terraform)
- Working directories
- Artifact names
- Conditional execution flags

This avoids copy-paste pipelines and enables safe customization.

---

### 3️⃣ Opinionated but Flexible
Templates enforce:
- Consistent structure
- Predictable behavior

…but still allow:
- Overrides where needed
- Project-specific customization

---

## 🔄 How Other Repositories Consume These Templates

Example usage from an application repo:

```yml
resources:
  repositories:
    - repository: cicdTemplates
      type: github
      name: Skandy01/azure-devops-pipeline-templates-enterprise
      ref: refs/tags/v1.0.0

stages:
- template: templates/stages/ci-stage.yml@cicdTemplates
  parameters:
    nodeVersion: '18.x'
    workingDirectory: 'frontend'

🛡️ Governance & Best Practices

Templates are immutable once versioned

Breaking changes require a major version bump

Security and quality steps can be enforced centrally

Teams consume templates — they don’t rewrite them

This model scales cleanly across large organizations.


> This repo is about building CI/CD as a shared platform capability.


👤 Author

Skand Tripathi
DevOps Engineer | Platform Engineering | CI/CD | Azure | DevSecOps
