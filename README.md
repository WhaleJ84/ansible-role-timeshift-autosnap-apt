timeshift-autosnap-apt
=========

Installs and configures [timeshift-autosnap-apt](https://github.com/wmutschl/timeshift-autosnap-apt) for the user.

Requirements
------------

The following collections are required:

- community.general

They can be installed by running `ansible-galaxy collection install $COLLECTION`.

To include this role in your `requirements.yml` file, add the following list item:

```yaml
---
roles:
  - name: whalej84.timeshift-autosnap-apt
    src: https://github.com/WhaleJ84/ansible-role-timeshift-autosnap-apt.git
    scm: git

  - name: whalej84.timeshift
    src: https://github.com/WhaleJ84/ansible-role-timeshift.git
    scm: git

collections:
  - community.general
```

The system package `git` is also required.

Role Variables
--------------

| Variable            | Default      | Description            |
| ------------------- | ------------ | ---------------------- |
| autosnap\_destdir   | ""           | Makefile files prefix  |
| autosnap\_lib\_dir  | ""           | Makefile config prefix |
| autosnap\_repo\_dir | "/$USER/opt" | Git repo destinaiton   |

Dependencies
------------

As the package is an addition to the [timeshift](https://github.com/linuxmint/timeshift) program, said software is required. It is included in the `requirements.yml` output above.

- whalej84.timeshift

Example Playbook
----------------

This example playbook shows how I would use this role, with custom variables to suit my needs.

```yaml
---
- hosts: localhost

  vars:
    # 'repo_dir' shared with:
    # - timeshift-autosnap-apt
    repo_dir: "{{ ansible_user_dir }}/Downloads/repositories"

  roles:
    - role: whalej84.timeshift-autosnap-apt
      vars:
        autosnap_repo_dir: "{{ repo_dir }}"
        snapshot_boot: "false"
        update_grub: "false"
        snapshot_description: "{created before call to APT}"
      tags: [ timeshift-autosnap-apt ]
```
