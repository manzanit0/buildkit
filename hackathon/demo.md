# Abraca-install

## Problem

Each Linux distribution has a different way to install files
Creating efficient layers often requires lots of searching the internet

Example:

```dockerfile
FROM alpine:3.20

# I have to look this up everytime. Maybe it is just me?
RUN apk update && \
  apk add curl jq && \
  rm -rf /var/cache/apk/*

ENTRYPOINT ["sh", "-c", "curl --silent https://randomuser.me/api | jq '.results[0]'"]
```

## Solution

```dockerfile
FROM alpine:3.20

INSTALL curl jq

ENTRYPOINT ["sh", "-c", "curl --silent https://randomuser.me/api | jq '.results[0]'"]
```
