# 🚀 Kubernetes Monitoring Stack – Prometheus, Alertmanager & Grafana (Manual Deployment, No Helm)

This project demonstrates a **fully manual setup** of a Kubernetes monitoring stack using **Prometheus, Alertmanager, Grafana, and Node Exporter as a DaemonSet** – all configured via YAML manifests without Helm.  

It is designed to help understand the **mechanics, architecture, and integrations** of monitoring in Kubernetes before moving to automation tools like Helm or Operators.

---

## 📂 Project Structure

```bash
monitoring/
├── prometheus/
│   ├── configMap.yml
│   ├── headlessService.yml
│   ├── svc.yml
│   ├── prometheus-rbac.yml
│   ├── prometheus-rules.yml
│   └── statefulSet.yml
├── alertmanager/
│   ├── configMap.yml
│   ├── headlessService.yml
│   ├── svc.yml
│   └── statefulSet.yml
├── grafana/
│   ├── secret.yml
│   ├── headlessService.yml
│   ├── svc.yml
│   └── statefulSet.yml
└── node-exporter/
    ├── daemonSet.yml
    └── svc.yml
```

# 🛠 Components Overview

## 1. Prometheus
- Deployed as a **StatefulSet** with persistent storage.  
- Exposed via **NodePort `:30090`** for external access.  
- Configured with:
  - Scraping rules for **Node Exporter**, **Prometheus itself**, and **Alertmanager**.  
  - Alerting rules forwarded to **Alertmanager**.  

---

## 2. Node Exporter
- Runs as a **DaemonSet** on all Kubernetes nodes.  
- Exposes system metrics (**CPU, memory, disk, network**) on **port 9101**.  
- Uses a **Headless Service (`ClusterIP: None`)** for Prometheus service discovery.  

---

## 3. Alertmanager
- Deployed as a **StatefulSet** with 2 replicas.  
- Handles alerts from Prometheus and forwards them via integrations (e.g., **Email, Slack**).  
- Supports configurable **routing, grouping, and silencing**.  

---

## 4. Grafana
- Deployed as a **StatefulSet** with persistent storage.  
- Exposed via **NodePort `:30300`**.  
- Configured with:
  - Default admin credentials (`admin/admin`) or via **Kubernetes Secret**.  
  - **Prometheus added as a data source** for dashboards.
 
# 📖 Documentation & Article

For a detailed step-by-step guide, check out the Medium article:  
👉 [Implementing a Prometheus & Grafana Monitoring Stack in Kubernetes – Manual Deployment (No Helm)](https://medium.com/@sonalijain0605/enhancing-kubernetes-monitoring-with-grafana-dashboards-alerting-no-helm-just-yaml-part-2-6f65987c6798)

