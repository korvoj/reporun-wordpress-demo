# RepoRun WordPress Example Stack

This is a minimal WordPress + MariaDB example stack for testing RepoRun.

It is designed to satisfy RepoRun v1 constraints:

- `docker-compose.yml` + `stack.yml` are present.
- No `ports`.
- No named Docker volumes.
- Persistent data is stored only under `.stack-data/`.
- CPU and RAM limits are declared for every service.
- Runtime values are injected through RepoRun environment values.
- No `env_file`.
- No `restart` policy.
- Public images only.

## Files

```text
docker-compose.yml
stack.yml
.env.example
.gitignore
README.md
```

## Required RepoRun environment values

Create these environment values in the RepoRun UI before deploy:

```text
WORDPRESS_DB_NAME=wordpress
WORDPRESS_DB_USER=wordpress
WORDPRESS_DB_PASSWORD=change-me-wordpress-password
MYSQL_ROOT_PASSWORD=change-me-root-password
```

Optional:

```text
WORDPRESS_TABLE_PREFIX=wp_
```

## Endpoint

`stack.yml` exposes the WordPress service as the primary endpoint:

```text
service: wordpress
port: 80
access: authenticated
```

You may change the access policy in `stack.yml` if you want to test other RepoRun endpoint modes.

## First deploy

After the first successful deploy, open the primary endpoint and complete the WordPress setup wizard.

WordPress files persist under:

```text
.stack-data/wordpress/
```

MariaDB data persists under:

```text
.stack-data/mariadb/
```

## Notes

This stack is for RepoRun platform testing, not hardened production WordPress hosting.
