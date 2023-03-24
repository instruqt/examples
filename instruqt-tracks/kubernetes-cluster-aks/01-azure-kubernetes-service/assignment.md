---
slug: azure-kubernetes-service
id: qsk228yb1fll
type: challenge
title: Azure Kubernetes Service (AKS) Sandbox
teaser: Example track that comes with an AKS cluster and workstation with kubectl
  and helm enabled.
notes:
- type: text
  contents: |-
    <center><img src="../assets/azure.png" width=200></center>
    Instruqt is your browser based, virtual labs platform for Azure workshops, demos, training and enablement.
tabs:
- title: Terminal
  type: terminal
  hostname: cloud-client
- title: Azure Login
  type: service
  hostname: cloud-client
  port: 80
difficulty: basic
timelimit: 3600
---

AKS On Demand
=============
We've spun up an AKS cluster and installed the **kubectl** and **helm** commands on your workstation.

Your AKS cluster name is **instruqt-cluster**.

Go ahead and try running some commands in the Terminal tab:

```bash
kubectl get nodes
```

You can copy this template and use it as a starting point for your own tracks that require AKS.
