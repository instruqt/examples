---
slug: auto-starting-screen
id: 57oahlhyynxt
type: challenge
title: ⚙️ Auto Starting Screen for Your Users
teaser: This example automatically starts screen with some preconfigured windows.
  It also includes some handy keyboard shortcuts for changing between windows.
notes:
- type: text
  contents: |-
    The [GNU Screen](https://www.gnu.org/software/screen/) program is a Terminal Multiplexer.

    You can use it within Instruqt to preserve a shell environment or running command across multiple challenges.
- type: text
  contents: "# Did you know?\nThe [GNU Screen](https://www.gnu.org/software/screen/)
    program was created in 1987.\n\nThe #1 Billboard Top Hot 100 song that year was
    [Walk Like an Egyptian](https://www.youtube.com/watch?v=Cv6tuzHUuuk) by the Bangles.
    \U0001F469‍\U0001F3A4\U0001F3B8"
tabs:
- title: Shell
  type: terminal
  hostname: shell
- title: Website
  type: service
  hostname: shell
  port: 8000
- title: .screenrc
  type: code
  hostname: shell
  path: /root/.screenrc
difficulty: basic
timelimit: 600
---
<style type="text/css" rel="stylesheet">
hr.cyan { background-color: cyan; color: cyan; height: 2px; margin-bottom: -10px; }
h2.cyan { color: cyan; }
</style>In this first challenge we have auto-started a screen session that is prepopulated with the correct windows and processes. You may use the code from this track to create a persistent shell with one or more virtual tabs (windows).

Let's get started!

I'm Just Here for the Code
==========================

Find the source code for this track in our examples repo. Click the link below to get the source code:

[Instruqt Examples Repo](https://github.com/instruqt/examples/tree/master/instruqt-tracks/persist-shell-session)

The setup script in the 01-auto-starting-screen directory can be copied and used in your own track.

Easy Navigation with Shift-Arrow Keys
=====================================

Click into the Instruqt Shell tab on the left and navigate between windows holding down `SHIFT` and the right and left arrow keys ⬅️➡️.

There are three windows open in the screen session. Window 0 is running a Python web server, window 1 is running htop, and window 2 has an interactive shell in it. You can preview the Python website on the **Website** tab.

The only shortcuts your users need to remember are **SHIFT-Left** and **SHIFT-Right**.<br>

Run Commands and View Log Output
================================

Try the following command in the `shell` window. Remember you'll need to use the SHIFT-arrowkey shortcut to get into the shell prompt.

```bash
curl http://localhost:8000
```

Now switch over to the `webserver` window. You'll see a new log entry for the connection you just made with the curl command.<br>

Warning - One Terminal Tab Per Host
=====================================

If you auto-start screen via the user's `~/.bashrc` file you should only have *one* Instruqt terminal tab per host. This is because every terminal tab will try and attach to the currently running screen session. If you need more tabs just run them inside of the screen session as shown in the example.<br>

How Does It Work?
=================

There are two files that you'll need to enable auto-start of a screen session. The first is the `~/.screenrc` file located in the user's home directory. Take a look at this file and you'll see all the configuration options.

The second config goes on the end of the `~/.bashrc` file, and it looks like this:

```bash
if [[ -z "$STY" ]]; then
   screen -xRR default
fi
```

Warning - You'll need to escape the dollar sign if you are using a HEREDOC to add this to your file. Here's how it should look in your setup script. This protects the dollar sign and prevents your STY variable from vanishing when the file is rendered:

```bash
cat >> ~/.bashrc << EOF
if [[ -z "\$STY" ]]; then
   screen -xRR default
fi
EOF
```

These three lines force screen to start a new session or attach to the existing one if it's already running. This will happen every time your user hits the refresh button on the Shell tab.

Once these files are generated, the setup will continue to work across multiple challenges in your track.

The source code for this track is available for you to use as a starting point in your own challenges.
