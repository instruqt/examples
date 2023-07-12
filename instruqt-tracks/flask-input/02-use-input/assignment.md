---
slug: use-input
id: 4ugjcgkwgxaf
type: challenge
title: Use Input
teaser: Now that we have input, lets do something with it
tabs:
- title: Terminal
  type: terminal
  hostname: ubuntu
  workdir: /root
difficulty: ""
---
Viewing input
===

During the setup of this challenge, an S3 bucket was created with the name you specified.
See for yourself!

```
aws s3 ls
```

If all went well, you should see a bucket with the following name:

[[ Instruqt-Var key="BUCKET_NAME" hostname="ubuntu" ]]