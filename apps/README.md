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

configure admin access:

https://docs.bitnami.com/aws/apps/discourse/configuration/change-default-email/
https://meta.discourse.org/t/how-to-reset-password-for-users-in-postgresql-database/246690/3

```
# at host:
kubectl exec -ti discourse-<pod> -- bash

# inside pod:
cd /opt/bitnami/discourse
RAILS_ENV=production bundle exec rails c

# inside rails console
User.find_by_username("user").update!(password: 'asdfasdfASDF1234!')
User.find_by_username("user").update!(email: 'admin@local.mail')
User.find_by_username("user").email= 'admin@local.mail'
User.find_by_username("user").email_tokens.create(email: 'admin@local.mail')
User.find_by_username("user").activate
User.find_by_username("user").save!
```

login using user `admin@local.mail` and password `asdfasdfASDF1234!`
