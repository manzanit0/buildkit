# Setup

```bash
# Build our modified buildkit
$ make images

# Start buildkit
$ docker run -p 1234:1234 --rm --name buildkitd --privileged moby/buildkit:local --addr tcp://0.0.0.0:1234

# Create remote builder for buildx
$ docker buildx create --driver remote tcp://localhost:1234 --name hackathon

# Build a project here with the builder
$ docker buildx --builder hackathon build . --tag random-user:latest --load
```
