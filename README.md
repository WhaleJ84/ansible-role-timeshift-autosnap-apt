timeshift-autosnap-apt
=========

Installs and configures [timeshift-autosnap-apt](https://github.com/wmutschl/timeshift-autosnap-apt) for the user.

Requirements
------------

The following collections are required:

- community.general

They can be installed by running `ansible-galaxy collection install $COLLECTION`.

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

As the package is an addition to the [timeshift](https://github.com/linuxmint/timeshift) program, said software is required.

- whalej84.timeshift

Example Playbook
----------------

    - hosts: localhost
      roles:
         - role: whalej84.timeshift-autosnap-apt
		   vars: autosnap_repo_dir: "/opt/timeshift-autosnap-apt"

