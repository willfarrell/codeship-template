# jet

## Build

```bash
docker build -t jet .
docker run --rm -d --name jet \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jet
```

