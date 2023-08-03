create a secret like this:

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
