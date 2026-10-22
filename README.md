# Phansible Role: PostgreSQL

[![CI](https://github.com/phansible/role-postgresql/actions/workflows/ci.yml/badge.svg)](https://github.com/phansible/role-postgresql/actions/workflows/ci.yml)

An Ansible Role that installs [PostgreSQL](http://www.postgresql.org/) on Ubuntu and Debian specifically created with [Phansible](http://phansible.com/) in mind.

## Requirements

- Ubuntu 22.04, 24.04 or 26.04, or Debian 12 or 13.
- Ansible 2.15 or newer.
- The `community.postgresql` collection (bundled with the `ansible` package, or `ansible-galaxy collection install community.postgresql`).
- Internet access to `apt.postgresql.org`. PostgreSQL comes from the official PGDG repository, which installs the latest major release.

## Role Variables

All variables live under one `postgresql` dictionary in `defaults/main.yml`. Override the whole dictionary, since Ansible does not merge dictionaries by default.

| Variable | Default | Description |
| --- | --- | --- |
| `postgresql.database` | `phansible` | Database to create, owned by `user`. |
| `postgresql.user` | `changme` | User (role) to create. |
| `postgresql.password` | `changme` | Password for `user`. |
| `postgresql.dump` | `""` | SQL file under `/vagrant/` loaded into `database` with `psql`. Empty skips the import. |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  become: yes
  vars:
    postgresql:
      database: app
      user: app
      password: secret
      dump: ""
  roles:
    - role-postgresql
```

## License

This role is released under the terms of the license specified in the repository or if not specified, under the [MIT license](https://raw.githubusercontent.com/phansible/role-postgresql/master/LICENSE).

## Author Information

This role was created in 2015 by [The Phansible Team & Contributors](https://github.com/phansible/role-postgresql/graphs/contributors), credits go also to [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/) and source of inspiration.
