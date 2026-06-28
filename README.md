# 🎨 color-app — Cloud-Native GitOps Showcase

A containerized Node.js web application engineered to demonstrate a zero-touch GitOps continuous delivery lifecycle—from strictly encrypted local edge routing to a live Microsoft Azure Kubernetes Service (AKS) data center.

> **Architecture Philosophy:** *The application code is trivial; the delivery envelope is production-grade.*

---

## 📐 High-Level Architecture

```text
 [ Local Dev Edge ]                          [ Cloud CI/CD Pipeline ]
 Browser (https://localhost)                 Git Push (main)
          │                                         │
          ▼                                         ▼
 [ NGINX Ingress ]  ◄── (Custom Root CA)     [ GitHub Actions Runner ]
          │                                    │          │
          ▼                                    │ (Build)  │ (Patch YAML)
 [ K8s Service ]                               ▼          ▼
          │                              [ Docker Hub ]   [ Git Commit ]
          ▼                                                   │
 [ Express Pod ]  ◄─── (Block Storage PVC)                    ▼
                                             [ Azure AKS Cluster ]
                                             (Public LoadBalancer)
