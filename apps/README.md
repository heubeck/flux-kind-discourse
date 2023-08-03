create a secret like this before bootstrapping:

```
---
apiVersion: v1
kind: Secret
metadata:
  name: docker-auth
  namespace: default
stringData:
  username: <your hub.docker.com username>
  password: <your hub.docker.com public-repos-only scoped token>
```
