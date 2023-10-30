---
title: "Access remote jupyter lab in local machine"
date: 2023-10-30
categories:
  - python
classes: wide
excerpt: In this blog I will try to share how to access remote jupyter lab in local machine
---

## Steps
1. SSH to remote machine
2. Install jupyter lab by `pip install jupyterlab`
3. Run jypyter lab by `jupyter lab --ip=0.0.0.0 --port=8888 --no-browser`
4. Access jupyter lab in local browser by URL `http://[INSTANCE_EXTERNAL_IP]:8888/lab`

Here `[INSTANCE_EXTERNAL_IP]` means your remote machine IP. It could be GCP instance or AWS machine.
