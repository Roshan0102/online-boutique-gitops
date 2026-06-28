# 🚀 Kubernetes-Native Cloud Project: GitOps & Application Delivery

![ArgoCD](https://img.shields.io/badge/ArgoCD-%23EF7B4D.svg?style=for-the-badge&logo=argo&logoColor=white)
![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![GitOps](https://img.shields.io/badge/GitOps-Operational_Model-%231F3059?style=for-the-badge)
![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)

Welcome to the **GitOps & Application Delivery** repository for the Kubernetes-Native Cloud Project. This repository acts as the single source of truth for the desired state of our applications and operational tools running on the Kubernetes (EKS) cluster. We use **ArgoCD** to automatically synchronize this state, ensuring continuous delivery and configuration drift prevention.

## 🌟 Key Application & Deployment Features

*   **🛒 CloudCart Microservices:** The core e-commerce application (`cloudcart`) seamlessly deployed and managed via GitOps pipelines.
*   **🗄️ Robust Database Architecture:** The application connects to a highly available, managed **Postgres RDS with a Standby Replica (Multi-AZ)**, ensuring automated failover, data redundancy, and uninterrupted user experience.
*   **📊 Monitoring & Observability:** Pre-configured `monitoring` (Prometheus/Grafana) and `logging` stacks are deployed alongside the application, including custom dashboards (`cloudcart-grafana-dashboard.json`).
*   **🔁 Automated Reconciliation:** ArgoCD continually monitors these manifests and reconciles the live cluster state with this repository.

## 📂 Repository Structure

*   `argocd/`: Contains the ArgoCD Application definitions that tell ArgoCD where to look and what to deploy.
*   `apps/`: The actual Kubernetes deployment manifests and Helm values.
    *   `apps/cloudcart`: CloudCart application services and configurations.
    *   `apps/monitoring`: Observability stack.
    *   `apps/logging`: Centralized logging configurations.

## 🔗 Related Repositories

This GitOps repository works hand-in-hand with our infrastructure repository to deliver a fully automated end-to-end cloud platform:

*   🚀 **GitOps Repo (Current):** [Roshan0102/online-boutique-gitops](https://github.com/Roshan0102/online-boutique-gitops)
*   🏗️ **Infrastructure Repo:** [Roshan0102/eks-platform-infra](https://github.com/Roshan0102/eks-platform-infra)

## 🛠️ How it Works

1. Developers or operators update manifests in this repository (e.g., bumping an image tag).
2. Changes are merged into the `main` branch.
3. ArgoCD detects the change and automatically syncs the new desired state to the EKS cluster.
