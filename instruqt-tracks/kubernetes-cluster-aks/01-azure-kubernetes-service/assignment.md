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
Azure Playground
================
This is a proof-of-concept track that includes a Windows workstation, a Linux workstation, Powershell, Visual Studio Code, an Azure subscription, and an AKS cluster.

Feel free to explore the different tabs on the left and use the environment for testing and development.

Azure GUI and az CLI
====================
You can access your Azure sandbox subscription with the login credentials found on the left. Go ahead and click the Subscription ID link to be taken to the Azure portal login page. You can use the Email and password that we have generated for you.

Want to try out the CLI as well? Click on the Terminal tab and run this command:

```
az vm create \
    --resource-group instruqtResourceGroup \
    --name instruqtVM \
    --image Win2022AzureEditionCore \
    --public-ip-sku Standard \
    --admin-username azureuser
```

You'll need to input a complex password of at least 12 characters in length. Congratulations, you just stood up a Windows Virtual Machine on Azure! Log onto the Azure Portal and see your VM in the UI if you wish.

Visual Studio Code
==================
Instruqt tracks can include the Code Server version of Visual Studio Code, which runs right in the web browser.

Now your students or participants can work with a full-featured IDE without having to install anything. Most marketplace extensions are supported and you can customize the interface with your own color and icon themes.

Windows Desktop
===============
Need a Windows Desktop environment? We've got you covered.  Click on the RDP tab on the left to access the Windows desktop through your browser. This is a VM running Windows Datacenter 2019, and it has tools like Powershell 7 and Visual Studio Code pre-installed.

Powershell
==========
Instruqt allows you to run a Powershell tab just like the Linux Terminal tab.  The `az` command also works here so you can access Azure from Linux or Windows Powershell command prompts.

AKS On Demand
=============
We've also spun up an AKS cluster and installed the **kubectl** and **helm** commands on your workstation.

Your AKS cluster name is **instruqt-cluster**.

Go ahead and try running some commands in the Terminal tab:

```bash
kubectl get nodes
```

You can copy this template and use it as a starting point for your own tracks that require AKS.

Juice Shop Sample App 🧃
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