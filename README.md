# vault-cci
Simple vault container for use in CircleCI 2.0

***DO NOT USE THIS IN A PRODUCTION SETTING***

In using this container you can gain access to the client token from outside the container using `curl`:

```
curl localhost:8021/.vault_token
```

This allows you to do whatever initialization/testing against vault, essentially getting aroung the lack of default client tokens.

## Example usage in CCI

```
version: 2.0
jobs:
  build:
    docker:
      - image: postgres:9.6
        environment:
          POSTGRES_USER: a-user
          POSTGRES_DB: a-secret
      - image: hopsoft/graphite-statsd
      - image: mannimal/vault-cci
  steps:
    - checkout
    - run:
        name: Setup Vault
        command:
```
