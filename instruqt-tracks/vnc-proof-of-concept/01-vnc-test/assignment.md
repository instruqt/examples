---
slug: vnc-test
id: xulhp5dulzwd
type: challenge
title: VNC Proof of Concept
teaser: This track shows you how to embed a Linux graphical desktop inside of Instruqt.  Try
  it now!
notes:
- type: text
  contents: VNC can be used to log onto a graphical desktop environment on Linux servers.
tabs:
- title: Terminal
  type: terminal
  hostname: ubuntu
- title: VNC - New Window
  type: website
  url: https://ubuntu.${_SANDBOX_ID}.instruqt.io:8443/vnc.html?host=ubuntu.${_SANDBOX_ID}.instruqt.io&port=8443
  new_window: true
- title: VNC - Embedded
  type: website
  url: https://ubuntu.${_SANDBOX_ID}.instruqt.io:8443/vnc.html?host=ubuntu.${_SANDBOX_ID}.instruqt.io&port=8443
difficulty: basic
timelimit: 600
---
Click on the **VNC - Embedded** or **VNC - New Window** tabs to log onto VNC. The password is `instruqt`.


You can also use your own VNC client to connect. Run the following command to get the server address:

```
echo $HOSTNAME.$INSTRUQT_PARTICIPANT_ID.instruqt.io:5901
```
