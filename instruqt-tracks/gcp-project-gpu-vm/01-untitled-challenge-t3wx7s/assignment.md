---
slug: untitled-challenge-t3wx7s
id: vx35nwf6p0a4
type: challenge
title: Accessing GPU instance
tabs:
- id: ul9mgwk4ocli
  title: GPU instance terminal
  type: terminal
  hostname: workstation
  cmd: gcloud compute ssh root@gpu-instance --zone=europe-west1-b --ssh-key-file=/root/.ssh/ssh_user
- id: vwlouz1jvlpr
  title: GPU instance service
  type: service
  hostname: workstation
  path: /
  port: 8888
- id: kgqxao8txdyi
  title: Cloud Console
  type: service
  hostname: workstation
  path: /
  port: 80
- id: lqi0iso6fndx
  title: Workstation
  type: terminal
  hostname: workstation
difficulty: ""
enhanced_loading: null
---
# Accessing GPU instance
In this sandbox, we have configured a GPU enabled VM instance, running in a GCP Project.

This track provisions a VM with an NVIDIA Tesla T4 GPU, by executing the following `gcloud` command from the `setup` script:

```bash,nocopy
# Provision GPU enabled instance, passing metadata ssh-keys and startup-script is optional
INSTANCE_NAME=gpu-instance
ZONE=europe-west1-b
IMAGE=projects/ubuntu-os-accelerator-images/global/images/ubuntu-accelerator-2404-amd64-with-nvidia-580-v20251021

gcloud compute instances create $INSTANCE_NAME \
    --zone=$ZONE \
    --machine-type=n1-standard-1 \
    --accelerator=count=1,type=nvidia-tesla-t4 \
    --create-disk=auto-delete=yes,boot=yes,device-name=$INSTANCE_NAME,image=$IMAGE,mode=rw,size=10,type=pd-balanced \
    --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=default \
    --tags=http-server \
    --maintenance-policy=TERMINATE \
    --metadata="ssh-keys=root:$(cat /root/.ssh/ssh_user.pub)"
```

We expose the GPU VM to the end user via GCP's Identity Aware Proxy. This allows us to set up a [button label="Terminal"](tab-0) and [button label="Service"](tab-1) tab, linking directly to the VM.

The GCP account only gives `roles/viewer` access to the end user, to prevent them from provisioning more resources. Admin credentials are used to provision the VM instance, set up SSH and IAP connectivity, and configure `nginx` as an example service.