# 📊 Kubernetes Monitoring Stack – Prometheus & Grafana (Manual Deployment)

A simple Kubernetes setup for **Prometheus** and **Grafana** monitoring using **manual YAML deployments**.  
No Helm charts — just the essentials for learning and customization.

---

## 📌 Overview
This repository demonstrates:
- Namespace creation for monitoring
- Prometheus deployment & service
- Grafana deployment & service
- Manual integration of Grafana with Prometheus

Designed for:
- Learning Kubernetes monitoring basics
- Gaining control over configurations
- Understanding service connectivity

---

## 🏗 Architecture
- **Prometheus** scrapes metrics from the Kubernetes cluster.
- **Grafana** visualizes the metrics from Prometheus.
- NodePort (or LoadBalancer/Ingress) provides external access.

---
## ✅ Prerequisites
- A running Kubernetes cluster (Minikube, kind, or cloud-based)
- `kubectl` CLI configured to access the cluster
- Basic understanding of Kubernetes resources

---
