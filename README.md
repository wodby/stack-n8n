# n8n application stack for Kubernetes on Wodby

Deploy n8n, the workflow automation tool, on Kubernetes with Wodby.

This repository defines the Wodby stack manifest and its default service
composition.

<!-- wodby:generated:start -->

## Stack contract

- [n8n stack on Wodby](https://wodby.com/stacks/n8n)
- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Service definitions

- [n8n service](https://github.com/wodby/service-n8n)
- [PostgreSQL service](https://github.com/wodby/service-postgres)
- [OpenSMTPD service](https://github.com/wodby/service-opensmtpd)

## What's included

| Component / service | Default configuration |
| --- | --- |
| n8n<br>`n8n` | required; enabled by default; links: `postgres` → `postgres`, `sendmail` → `opensmtpd` |
| PostgreSQL<br>`postgres` | required; enabled by default; volumes: `data` 10 GB |
| OpenSMTPD<br>`opensmtpd` | optional; disabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Validate the stack manifest

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

<!-- wodby:generated:end -->

## Deploy this stack

Set the n8n service's Owner email and Owner password when creating the
application. n8n applies them on every start, so its setup page is never open
to the public. Webhooks use the application's domain.

n8n sends user invitations and password resets by email. Enable OpenSMTPD to
send them.

Back up the PostgreSQL database before upgrading n8n: newer versions migrate
it, and older versions can't use it afterwards.

## Maintain a custom version

1. Fork this repository.
2. Edit `stack.yml`.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target.
Stack-local names and referenced service names are distinct identifiers.
