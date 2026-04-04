# 🚀 Reusable CI/CD Workflows (GitHub Actions)

## 📌 Overview

This repository contains **reusable GitHub Actions workflows and composite actions** designed to standardize CI/CD pipelines across multiple projects.

It enables **modular, scalable, and consistent pipeline execution** using `workflow_call`.

---

## 🧠 Key Features

* Reusable workflows for different environments:

  * Feature
  * Dev
  * Non-Prod
* Custom composite action to **update commit status**
* Commit-based versioning using **Git SHA**
* Integrated **Docker build, security scan, and deployment**
* AWS ECR + EKS integration
* Helm-based deployments

---

## 📂 Structure

```id="a1b2c3"
.github/
│
├── actions/
│   └── update-commit-status/
│       └── action.yaml
│
└── workflows/
    ├── feature-nodejs-pipeline.yaml
    ├── dev-nodejs-pipeline.yaml
    └── non-prod-pipeline.yaml
```

---

## ⚙️ Reusable Workflow Usage

Projects can call reusable workflows like this:

```yaml id="b2c3d4"
jobs:
  dev-pipeline:
    uses: org/repo/.github/workflows/dev-nodejs-pipeline.yaml@main
    with:
      project: roboshop
      component: catalogue
      environment: dev
    secrets: inherit
```

---

## 🔁 Commit Status Updates

We use a **custom composite action** to update commit statuses:

* UNIT_TESTS
* DOCKER_BUILD
* SECURITY_CHECK
* DEPLOY

This improves visibility directly in GitHub UI.

---

## 🔐 Security

* Integrated **Trivy scanning**
* Blocks pipeline on HIGH/CRITICAL vulnerabilities
* Ensures secure container images before deployment

---

## 🐳 Versioning Strategy

* Uses **short commit SHA (9 chars)** as image tag
* Ensures traceability between code and deployment

---

## ☁️ Deployment Flow

1. Build Docker image
2. Run security scan
3. Push to AWS ECR
4. Deploy to EKS using Helm

---

## 🚀 Benefits

* Reusability across projects
* Reduced duplication
* Standardized CI/CD
* Better observability via commit status

---

## 👨‍💻 Author

Sai Pavan Penke  – DevOps Engineer
