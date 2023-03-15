---
slug: azure-kubernetes-service
id: ebjhrynnzrcr
type: challenge
title: Azure Sandbox
teaser: Example track that comes with an Azure account and a Linux workstation
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
difficulty: basic
timelimit: 3600
---
Azure Playground
================
This is a proof-of-concept track that includes a Linux workstation with an Azure subscription.

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
