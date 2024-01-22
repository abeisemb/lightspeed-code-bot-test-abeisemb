# PHP Roles Collection for Ansible

**DEPRECATED**: Due to the maintenance burden of trying to manage this collection in addition to the `php_*` roles, and my inability to move everything into the `geerlingguy.php` namespace, I have deprecated this collection and recommend you use my `php_*` roles (e.g. `geerlingguy.php`, `geerlingguy.php_version`, etc.) individually instead.

[![MIT licensed][badge-license]][link-license]
[![Galaxy Collection][badge-collection]][link-galaxy]
[![CI][badge-gh-actions]][link-gh-actions]

This collection contains all the PHP-related roles maintained by Jeff Geerling (geerlingguy).

It includes:

  - [geerlingguy.php](https://galaxy.ansible.com/geerlingguy/php)
  - [geerlingguy.php_memcached](https://galaxy.ansible.com/geerlingguy/php-memcached)
  - [geerlingguy.php_mysql](https://galaxy.ansible.com/geerlingguy/php-mysql)
  - [geerlingguy.php_pear](https://galaxy.ansible.com/geerlingguy/php-pear)
  - [geerlingguy.php_pecl](https://galaxy.ansible.com/geerlingguy/php-pecl)
  - [geerlingguy.php_pgsql](https://galaxy.ansible.com/geerlingguy/php-pgsql)
  - [geerlingguy.php_redis](https://galaxy.ansible.com/geerlingguy/php-redis)
  - [geerlingguy.php_tideways](https://galaxy.ansible.com/geerlingguy/php-tideways)
  - [geerlingguy.php_versions](https://galaxy.ansible.com/geerlingguy/php-versions)
  - [geerlingguy.php_xdebug](https://galaxy.ansible.com/geerlingguy/php-xdebug)
  - [geerlingguy.php_xhprof](https://galaxy.ansible.com/geerlingguy/php-xhprof)

## Usage

Install this collection locally:

    ansible-galaxy collection install geerlingguy.php_roles -p ./collections

Then you can use the roles from the collection in your playbooks:

```yaml
---
- hosts: all

  collections:
    - geerlingguy.php_roles

  roles:
    - php
    - role: php-versions
      vars:
        php_version: '7.3'
```

> If you want to be more explicit, you can use the fully-qualified role name when referring to a role in this collection, like `geerlingguy.php_roles.php` instead of just `php`. This could be helpful if, for example, you maintain a separate `php` role in another place on your local workstation.

## Development

Currently, all the PHP roles (inside `roles/`) are Git submodules, and work on the roles themselves should take place in the upstream Role repository. At some point, the roles might move into this repository for their canonical home.

This collection has some integration tests (inside `tests/`), however, which pull all the roles together and ensure they work in tandem on the latest supported platforms.

The integrated tests use `ansible-test`. You can run them with the following command:

```
ansible-test integration --docker geerlingguy/docker-ubuntu1804-ansible
```

> Note: You can switch out `ubuntu1804` with any other supported operating system (e.g. `centos7`).

### Pushing a new version

Before tagging a new version, make sure all the git submodules are up to date:

```
git submodule update --recursive --remote
```

Then commit and push all changes, and make sure all tests are passing.

Then tag the new version of the collection and push the tag.

Once pushed, GitHub actions will run the `galaxy-deploy.yml` playbook to deploy the new version.

## Author

This collection was created in 2019 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/) and [Ansible for Kubernetes](https://www.ansibleforkubernetes.com).

[badge-gh-actions]: https://github.com/geerlingguy/ansible-collection-php_roles/workflows/CI/badge.svg?event=push
[link-gh-actions]: https://github.com/geerlingguy/ansible-collection-php_roles/actions?query=workflow%3ACI
[badge-collection]: https://img.shields.io/badge/collection-geerlingguy.php_roles-blue
[link-galaxy]: https://galaxy.ansible.com/geerlingguy/php_roles
[badge-license]: https://img.shields.io/github/license/geerlingguy/ansible-collection-php_roles.svg
[link-license]: https://github.com/geerlingguy/ansible-collection-php_roles/blob/master/LICENSE
[badge-gh-actions]: https://github.com/geerlingguy/ansible-role-homebrew/workflows/CI/badge.svg?event=push
