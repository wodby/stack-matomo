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

## Service definitions

- [Matomo service](https://github.com/wodby/service-matomo)
- [MariaDB service](https://github.com/wodby/service-mariadb)
- [NFS provisioner service](https://github.com/wodby/service-nfs-provisioner)
- [OpenSMTPD service](https://github.com/wodby/service-opensmtpd)

## What's included

| Component / service | Default configuration |
| --- | --- |
| Matomo<br>`matomo` | required; enabled by default; volumes: `files` 5 GB; links: `db` → `mariadb`, `files` → `files-nfs`, `sendmail` → `opensmtpd` |
| MariaDB<br>`mariadb` | optional; enabled by default; volumes: `data` 20 GB |
| Files NFS storage<br>`files-nfs` | optional; enabled by default; volumes: `data` 10 GB |
| OpenSMTPD<br>`opensmtpd` | optional; enabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Validate the stack manifest

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

<!-- wodby:generated:end -->

## Deploy this stack

The stack runs the prebuilt [Matomo image](https://github.com/wodby/matomo); there is no repository to connect or build
to wait for.

Enter the superuser's password and email, and optionally a username and the address of the first website to track, in
the Matomo service's settings when you create the app. The first deployment installs Matomo with that account; Matomo's
web installer is not used. Reports are archived every hour by the service's cron job.

Matomo's settings file, custom logos and Marketplace plugins are kept on the shared `files` volume: back it up together
with the database.

## Maintain a custom version

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target
and derivative reference. Stack-local names and referenced service names are
distinct identifiers.
