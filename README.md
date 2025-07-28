# Voltage Park Kubernetes Demo

[Voltage Park](https://voltagepark.com) provides powerful GPU infrastructure that can be orchestrated via Kubernetes just like any other cloud. This repository contains a minimal, self-contained example you can follow end-to-end to get a demo application running on a Voltage Park GPU cluster.

---

## 📽️ Demo Walk-Through (YouTube)

<!-- Replace the VIDEO_ID below with the actual ID once the video is published -->
<p align="center">
  <a href="https://www.youtube.com/watch?v=VIDEO_ID" target="_blank">
    <img src="https://img.youtube.com/vi/VIDEO_ID/hqdefault.jpg" alt="Voltage Park Kubernetes Demo – YouTube video thumbnail" width="640" />
  </a>
</p>

---

## 🗺️ Repository Contents

| Path | Description |
|------|-------------|
| `demo.yaml` | A single-file Kubernetes manifest that deploys the demo application and required resources. |

Feel free to copy-paste this manifest or adapt it for your own workloads.

---

## 🚀 Quick Start

1. **Create a Voltage Park cluster** (if you haven’t already).
   ```bash
   # Example – adjust specs to your needs
   vp create-cluster demo-cluster --nodes 2 --gpu a100-80gb
   vp get-kubeconfig demo-cluster > kubeconfig.demo
   export KUBECONFIG=$PWD/kubeconfig.demo
   ```
2. **Verify you can reach the cluster**:
   ```bash
   kubectl get nodes
   ```
3. **Deploy the demo application**:
   ```bash
   kubectl apply -f demo.yaml
   ```
4. **Watch it come online**:
   ```bash
   kubectl get pods -w
   ```
5. **Clean up** when you’re done:
   ```bash
   kubectl delete -f demo.yaml
   # or delete the whole cluster
   vp delete-cluster demo-cluster --yes
   ```

---

## 📝 Prerequisites

- A Voltage Park account with API access
- `kubectl`configured locally