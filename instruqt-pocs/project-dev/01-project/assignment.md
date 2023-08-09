---
slug: project
id: hxl3epr8t4ss
type: challenge
title: XL release, Ansible Tower, Git Server and Jenkins
notes:
- type: text
  contents: |
    # **Overview of Developer Experience project**

    ![DeveloperExperienceproject.png](../assets/DeveloperExperienceproject.png)
tabs:
- title: git-shell
  type: terminal
  hostname: git-jenkins-server
- title: Shell-Local
  type: terminal
  hostname: local-system
- title: ansible
  type: service
  hostname: ansibletower
  path: /
  port: 443
- title: xlrelease
  type: service
  hostname: xlrelease
  path: /
  port: 5516
  url: http://signin.aws.amazon.com/
- title: jenkins
  type: website
  url: http://git-jenkins-server.${_SANDBOX_ID}.instruqt.io:8080
  new_window: true
difficulty: basic
timelimit: 600
---
We have preprovisioned 4 VM's Git Server & Jenkins, XL release, Ansible Tower and Client server.

Ansible Tower
===

- Login to Ansible Tower with credentials:  **username:** `admin` , **password:** `password`
- Open credentials tab, Click on the `+` button to add new credentials and enter the follwing details:
- **NAME**: `git`
- **CREDENTIAL TYPE**: `Source Control`
- **USERNAME**: `gituser`
- **PASSWORD**: `password`,
- Click **Enter** button on keyboard after providing password
- Or else Click on **save** to save the details.
![image.png](../assets/image.png)
##  Open projects tab, Click on the Demo Project and edit the follwing details:

- **SCM URL**:
```
http://gituser@[[ Instruqt-Var key="url" hostname="git-jenkins-server" ]]/project.git
```
- **SCM CREDENTIAL**: `git`
![image.png](../assets/git_credentials.png)
- Click on **Save**
##  Open Templates, Click on the Demo job template and edit the follwing details:
- Clicimage.pngk on **PLAYBOOK** dropdown and select the playbook (demo_playbook.yml)
![](../assets/git_credentials.png)
- As of now we had a demo_playbook.yml pushed in repo, So Add it to Start the **JOB** using the **Template**


XL release steps
===

- Open  **XL release** in **tabs** with credentials:  **username:** `admin` , **password:** `admin`
- click on **folder**
- click on **Samples & Tutorials**
![image.png](../assets/image.png)
- Click on **template** with named **Applications/XL_Test**  which we have created as a sample template
- Now click on **Jenkins task** which is added already.
![image.png](../assets/image.png)
- Now click on `Config`.
- **Select Server**:  `Jenkins Server` from dropdown menu
- **Job**: `JenkinsTestJob`
![image.png](../assets/image.png)

Now close the window.

**Next we need to  create a trigger**.

- Click on **Triggers** in left side panel.
![image.png](../assets/image.png)
- Click on Add **Trigger**.
- Update the mandatory fields like **Title**,
- Select **trigger type** as `Git: Poll`,
- **Pole interval** : `5`,
- Select your **Repository** (here we have created a Git connection with name `Git Server`).
-  **Branch**: master
![image.png](../assets/image.png)
![image.png](../assets/image.png)
- Select your **template:** Applications/XL_Test and  **folder:** Samples & Tutorials
- Enter mandatory field **Release Title** (as per your choice)
- **click** on Save
![image.png](../assets/image.png)


 Workflow
===

Go to the **Shell_local** tab
- cd project/
- Make some changes in `demo_playbook.yml`  using
```
vi demo_playbook.yml
```
After you made changes, then push to the git server
```
git add .
git commit -m "First commit"
git push origin master
```

Now check the flow on XL release, Jenkins and Ansible Tower.
Open  **Jenkins** in **tabs** with credentials:  **username:** `admin` , **password:** `admin`
XL release trigger jenkins when there is a commit in git repo, jenkins builds job and deploys to ansible tower.

Outputs should look like:
- In **Jenkins:**
![image.png](../assets/image.png)
- In **Ansible:**
**Jobs:**
![image.png](../assets/image.png)
**Dashboard:**
![image.png](../assets/image.png)
- In **XL Release:**
![image.png](../assets/image.png)