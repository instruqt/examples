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
    <center><img src="../assets/azure.png" width=600></center>

    Instruqt is your browser based, virtual labs platform for Azure workshops, demos, training and enablement.
tabs:
- title: Azure Login
  type: service
  hostname: cloud-client
  port: 80
- title: Terminal
  type: terminal
  hostname: workstation
- title: Code Server IDE
  type: service
  hostname: workstation
  port: 8443
- title: RDP
  type: service
  hostname: guac
  path: /#/client/c/windows?username=instruqt&password=Passw0rd!
  port: 8080
- title: PowerShell
  type: terminal
  hostname: windows
- title: Juice Shop
  type: service
  hostname: workstation
  port: 3000
difficulty: basic
timelimit: 3600
---
We've spun up an AKS cluster and installed the **kubectl** and **helm** commands on your workstation.

The Azure `az` command line tool is also installed and ready to use.

Your AKS cluster name is **instruqt-cluster**.

Go ahead and try running some commands:

```bash
kubectl get nodes
```

You can copy this template and use it as a starting point for your own tracks that require AKS.

Install the Juice Shop 🧃
=========================

Now let's install the Juice Shop application in your cluster with the following commands:

```bash
helm repo add securecodebox https://charts.securecodebox.io/
helm install my-juice-shop securecodebox/juice-shop --version 3.6.0
```

It can take up to 30 seconds for the application to start. Check if the app is ready with the following command:

```bash
kubectl get pods --watch
```

When you see the `STATUS` change to `Running` the Juice Shop is open for business! Press **CTRL-C** on your keyboard to stop the kubectl command and return to the command prompt.

Expose the port with the following command:

```bash
kubectl --address 0.0.0.0 port-forward service/my-juice-shop 3000:3000
```

Now you can click on the **Juice Shop** tab to see the Juice Shop running.

The OWASP Juice Shop is a sample site used to demonstrate bad and insecure web design!

With Instruqt you can easily install and manage your own Kubernetes application or service.