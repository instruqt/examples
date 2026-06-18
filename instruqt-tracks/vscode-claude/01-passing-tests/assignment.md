---
slug: passing-tests
type: challenge
title: Passing tests
teaser: Use Claude Code with AWS Bedrock to fix broken code
tabs:
- title: Code editor
  type: service
  hostname: workstation
  port: 8080
- title: Terminal
  type: terminal
  hostname: workstation
  workdir: /root/project
difficulty: basic
timelimit: 600
enhanced_loading: null
---

Environment Setup
=================

This sandbox uses an **Instruqt cloud account** to provision a real AWS account automatically when the challenge starts. You don't need to supply any credentials — they are injected into the container at boot.

**What gets provisioned:**

- An AWS account scoped to the Bedrock service in multiple US/CA regions (`us-east-1`, `us-east-2`, `us-west-1`, `us-west-2`, `ca-central-1`, `ca-west-1`)
- The `AmazonBedrockLimitedAccess` managed IAM policy, which grants access to invoke Bedrock foundation models (including Claude) but nothing else — see [available models](https://docs.instruqt.com/ai-capabilities/connect-ai-models#amazon-bedrock)

**How it's wired in:**

1. The container image (`gcr.io/instruqt/vscode-claude:latest`) runs [code-server](https://coder.com/docs/code-server) — a browser-based VS Code — on port 8080
2. Instruqt injects `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY` as environment variables into the container using the provisioned account credentials
3. A custom [entrypoint script](https://github.com/instruqt/docker-vscode-claude/blob/main/entrypoint.sh) runs at container startup. It reads the injected AWS credentials from the environment and writes them — along with `CLAUDE_CODE_USE_BEDROCK=1` — into `~/.claude/settings.json` under the `"env"` key:

   ```json
   {
     "env": {
       "CLAUDE_CODE_USE_BEDROCK": "1",
       "AWS_REGION": "<injected>",
       "AWS_ACCESS_KEY_ID": "<injected>",
       "AWS_SECRET_ACCESS_KEY": "<injected>"
     }
   }
   ```

   Writing credentials here (rather than relying solely on shell environment variables) ensures Claude Code picks them up regardless of which terminal session or VS Code panel invokes it. The entrypoint then launches code-server.

4. The image ships a VS Code [settings.json](https://github.com/instruqt/docker-vscode-claude/blob/main/settings.json) that disables the built-in Copilot/chat AI features and suppresses the Claude Code login prompt, since authentication is handled via Bedrock rather than a Claude.ai account:

   ```json
   {
     "chat.disableAIFeatures": true,
     "claudeCode.disableLoginPrompt": true
   }
   ```

   Without `chat.disableAIFeatures`, VS Code would surface its own AI chat UI alongside Claude Code. Without `claudeCode.disableLoginPrompt`, the extension would ask learners to log in to Claude.ai on every start — unnecessary (and misleading) when Bedrock credentials are already present.

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
