## Sudoroom Server Management

This repository is for documentation and management scripts related to
Sudoroom's servers and other online infrastructure.

### Overview

The server deployment and management package [Ansible](https://docs.ansible.com/) is used to define the desired configuration of the following servers:

* Wolf
  - Mailing lists
  - Wiki
  - sudoroom.org website

These Ansible playbooks are intended to be the one source of truth for how the servers are configured. Admins are strongly encouraged to incorporate changes to the configuration of the servers into the Ansible playbooks, and to not manually edit configs. The Ansible playbooks are idempotent, so re-running them on a running server will only alter the configurations that need to change to bring them up-to-date, and otherwise not touch anything else.

### How to Use

1. Install ansible
1. Set up an ssh key with the server
1. Check out the repo
1. Change directory to the ansible folder of the repo: `$ cd server-management/ansible/`
1. Run the desired playbook: `$ ansible-playbook playbooks/install-wolf.yml`

If you are setting up a brand-new server, there are some initial manual steps that must be completed before a playbook can be run. See the comments inside each playbook for details.

### Secrets

Some parts of the playbooks contain secrets (e.g. mariadb user passwords). These are stored as encrypted (vaulted) variables, and the password to the vault is not published (for hopefully obvious reasons). If you need to use these playbooks, contact an existing sysadmin for the vault password.
