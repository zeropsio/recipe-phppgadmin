# ZEROPS RECIPES

The concept of pre-prepared skeletons demonstrates the way how to set up and use technologies Zerops is supporting.

## phpPgAdmin 7.13.0

[phpPgAdmin](https://github.com/phppgadmin/phppgadmin) is a mature web-based administration tool for the PostgreSQL database.

## Zerops import syntax

```yaml
services:
  # Service will be accessible through zcli VPN under: http://phppgadmin
- hostname: phppgadmin
  # Type and version of a used service.
  type: php-apache@7.4
  # Whether the service will be run on one or multiple containers.
  # Since this is a utility service, using only one container is fine.
  mode: NON_HA
  # Folder name used as the root of the publicly accessible web server content.
  documentRoot: public
  # Repository that contains phpPgAdmin code with build and deploy instructions.
  buildFromGit: https://github.com/zeropsio/recipe-phppgadmin@main
  # Setting of the "DATABASE_HOSTNAME" environment variable.
  # It specifies the chosen hostname for the Zerops PostgreSQL service that should be managed.
  envVariables:
  - key: DATABASE_HOSTNAME
    # Here, the Zerops PostgreSQL service's chosen hostname is "postgresql".
    # Change it if you need to use a different one.
    content: postgresql
```

See the [Zerops documentation](https://docs.zerops.io/documentation/export-import/project-service-export-import.html) to understand how to use it.
