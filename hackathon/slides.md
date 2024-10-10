# Abraca-install

A terminal based presentation tool

---

## Problem (1)

Each Linux distribution has a different way to install files and I find myself
googling this every single time.

---

## Problem (2)

Creating high-quality Docker images requires some level of know-how, i.e.
removing cache layer.

---

## Problem (3)

I created my Dockerfile using a bulky ubuntu image, but my colleague suggested
I use alpine. Now I have to rewrite half of the Dockerfile.

### Example


```dockerfile
FROM alpine:3.20

# I have to look this up everytime. Maybe it is just me?
RUN apk update && \
    apk add curl jq && \
    rm -rf /var/cache/apk/*

ENTRYPOINT ["sh", "-c", "curl --silent https://randomuser.me/api | jq '.results[0]'"]
```

```dockerfile
FROM debian:12-slim

RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    apt-get install -y --no-install-recommends curl jq && \
  	rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["sh", "-c", "curl --silent https://randomuser.me/api | jq '.results[0]'"]
```

## Conclusion

* Would you find this useful?
* If you would, vote for us! :D
