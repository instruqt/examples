---
slug: passing-tests
id: qyxigqikpyki
type: challenge
title: Passing tests
teaser: Use Claude Code with AWS Bedrock to fix a failing test
tabs:
- id: 0e39zqtyjvl5
  title: Code editor
  type: service
  hostname: workstation
  port: 8080
- id: zydvggpjbvub
  title: Terminal
  type: terminal
  hostname: workstation
  workdir: /root/project
difficulty: basic
timelimit: 600
enhanced_loading: null
---

Step 1
======

Claude Code is already running in this environment, connected to AWS Bedrock — no Claude subscription needed.

Open the Claude Code panel and ask it to run the tests and explain what's failing.

Step 2
======

Ask Claude Code to fix the failing test in `src/sum.ts`. It will suggest a code change — review it and apply the fix.

Check
=====

To complete this challenge, press **Check**. It will run the tests and pass if all tests are passing.
