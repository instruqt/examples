---
slug: explore-kubernetes
type: challenge
title: Explore Kubernetes
teaser: Explore Kubernetes
notes:
- type: text
  contents: |-
    This track shows a multi-node Kubernetes cluster with one server
    and two worker nodes.

    Please wait while we provision the sandbox.
tabs:
- title: Server A
  type: terminal
  hostname: server-a
- title: Kubernetes Dashboard A
  type: service
  hostname: server-a
  path: /api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#!/
  port: 8001
- title: Server B
  type: terminal
  hostname: server-b
- title: Kubernetes Dashboard B
  type: service
  hostname: server-b
  path: /api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#!/
  port: 8001
difficulty: basic
timelimit: 600
---

👋 Introduction
===============

To complete this track, use `kubectl` to
print all nodes in the cluster.

📄 Step 01
==========

List the three nodes in the cluster

```
kubectl get nodes
```

🧩 Step 02
==========

Open the second tab (next to the terminal) with the Kubernetes Dashboard.

To login, use the token you can print with this command:

```
./token.sh
```

🏁 Finish the track
===================

Press **Check** to finish the track.
