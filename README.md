# Matomo application stack for Kubernetes on Wodby

Deploy Matomo applications on Kubernetes with Wodby.

This repository defines the Wodby stack manifests and default service
composition for Matomo.

<!-- wodby:generated:start -->

## Stack contract

- [Matomo stack on Wodby](https://wodby.com/stacks/matomo)
- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Matomo stack guide](https://wodby.com/docs/2.0/stacks/catalog/matomo/)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Start from a boilerplate

Use one of the compatible boilerplates exposed by this stack's services to
start with Wodby CI build configuration:

- [Vanilla Matomo](https://github.com/matomo-org/matomo)

## Service definitions

- [PHP (Matomo 5) service](https://github.com/wodby/service-matomo)
- [Nginx (Matomo) service](https://github.com/wodby/service-matomo-nginx)
- [MariaDB service](https://github.com/wodby/service-mariadb)
- [OpenSMTPD service](https://github.com/wodby/service-opensmtpd)
- [Valkey service](https://github.com/wodby/service-valkey)

## What's included

| Component / service | Default configuration |
| --- | --- |
| Matomo<br>`matomo` | required; enabled by default; links: `db` → `mariadb`, `sendmail` → `opensmtpd` |
| Nginx<br>`nginx` | required; enabled by default; links: `backend` → `matomo` |
| MariaDB<br>`mariadb` | optional; enabled by default; volumes: `data` 20 GB |
| OpenSMTPD<br>`opensmtpd` | optional; enabled by default |
| Valkey<br>`valkey` | optional; disabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Validate the stack manifest

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

<!-- wodby:generated:end -->

## Deploy this stack

Start from [Vanilla Matomo](https://github.com/matomo-org/matomo), or connect your own compatible source
repository.

Review service versions, storage, links, and optional components when creating
the application. The same stack can be reused across development, staging, and
production environments.

## Maintain a custom version

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target
and derivative reference. Stack-local names and referenced service names are
distinct identifiers.
