FROM alpine:3.20

INSTALL curl jq

ENTRYPOINT ["sh", "-c", "curl --silent https://randomuser.me/api | jq '.results[0]'"]
