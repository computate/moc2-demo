
# Installing FreeIPA in Kubernetes

```bash
oc --as system:admin create namespace computate-freeipa
oc project computate-freeipa
```

##  Create a secret

```bash
oc create secret generic freeipa-server-password \
  --from-literal admin.password="$(tr -dc 'A-Za-z0-9' < /dev/urandom | head -c 16)"
```

