---
title: Splunk - Set up
tags:
  - Splunk
  - SIEM
---

```
docker run --platform=linux/amd64 \
  --privileged -d -p 8000:8000 \
  -e SPLUNK_PASSWORD=<PASSWORDHEREEE> \
  -e SPLUNK_START_ARGS="--accept-license" \
  -e SPLUNK_GENERAL_TERMS="--accept-sgt-current-at-splunk-com" \
  --name so1 \
```

