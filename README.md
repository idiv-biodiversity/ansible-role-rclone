Ansible Role: rclone
====================

An Ansible role to install [rclone][].

Table of Contents
-----------------

<!-- toc -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
  * [Top-Level Playbook](#top-level-playbook)
  * [Role Dependency](#role-dependency)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

Requirements
------------

- Ansible 2.9

Role Variables
--------------

Without the following variables, rclone will be installed from the package
manager of the target hosts distro. Because not all distros are immediately up
to date, you can install the bleeding edge binary release from GitHub with
these variables:

```yml
# use this to force using binary GitHub release instead of package manager
rclone_version: 1.64.1

# these are from defaults/main.yml
rclone_binary_install_bin_dir: /usr/local/bin
rclone_binary_install_cache_dir: /var/cache
```

Dependencies
------------

```yml
---

# requirements.yml

roles:

  # optional: only for RHEL et al. distro install
  # - src: geerlingguy.repo-epel

  - name: idiv_biodiversity.rclone
    src: https://github.com/idiv-biodiversity/ansible-role-rclone
    version: v1.0.0

...
```

Example Playbook
----------------

### Top-Level Playbook

Write a top-level playbook:

```yml
---

- name: file transfer servers
  hosts: transfer
  roles:
    - role: idiv_biodiversity.rclone
      tags:
        - rclone

...
```

### Role Dependency

Define the role dependency in `meta/main.yml`:

```yml
---

dependencies:

  - role: idiv_biodiversity.rclone
    tags:
      - rclone

...
```

License
-------

MIT

Author Information
------------------

This role was created in 2017 by [Christian Krause][author] aka [wookietreiber
at GitHub][wookietreiber], HPC cluster systems administrator at the [German
Centre for Integrative Biodiversity Research (iDiv)][idiv].


[rclone]: https://rclone.org
[author]: https://www.idiv.de/staff/christian-krause/
[idiv]: https://www.idiv.de/
[wookietreiber]: https://github.com/wookietreiber
