
# Install the MOC 2.0 auth demo

## Switch to the computate-freeipa namespace in the test cluster

```bash
oc project computate-freeipa
```

##  Create a keycloak database secret

```bash
oc --as system:admin create secret generic postgres-pguser-keycloak \
  --from-literal user=keycloak \
  --from-literal password="$(tr -dc 'A-Za-z0-9' < /dev/urandom | head -c 16)"
```

## Install lldap

```bash
oc --as system:admin apply -k lldap/base/
```

## Install crunchy-postgres-operator

```bash
oc --as system:admin apply -k crunchy-postgres-operator/base/
```

## Install postgres

```bash
oc --as system:admin apply -k postgres/base/
```

## Install keycloak database setup job

```bash
oc --as system:admin apply -k keycloak/database-setup/
```

## Install keycloak

```bash
oc --as system:admin apply -k keycloak/base/
```
