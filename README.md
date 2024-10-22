[![CI](https://github.com/de-it-krachten/ansible-role-gitlab_cli/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-gitlab_cli/actions?query=workflow%3ACI)


# ansible-role-gitlab_cli

Installs the Gitlab CLI



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 39
- Fedora 40

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Version of the CLI to install
gitlab_cli_version: latest

# Gitlab CLI - API
gitlab_cli_api: https://gitlab.com/api/v4/projects/gitlab-org%2Fcli

# Gitlab CLI - repo
gitlab_cli_repo: https://gitlab.com/gitlab-org/cli

# Package name by OS family
gitlab_cli_package:
  RedHat: glab_{{ gitlab_cli_version }}_{{ ansible_system }}_{{ ansible_architecture }}.rpm
  Suse: glab_{{ gitlab_cli_version }}_{{ ansible_system }}_{{ ansible_architecture }}.rpm
  Debian: glab_{{ gitlab_cli_version }}_{{ ansible_system }}_{{ ansible_architecture }}.deb
  Alpine: glab_{{ gitlab_cli_version }}_{{ ansible_system }}_{{ ansible_architecture }}.apk

# Package download link
gitlab_cli_url: >-
  {{ gitlab_cli_repo }}/-/releases/v{{ gitlab_cli_version }}/downloads/{{ gitlab_cli_package[ansible_os_family] }}
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'gitlab_cli'
  hosts: all
  become: 'yes'
  tasks:
    - name: Include role 'gitlab_cli'
      ansible.builtin.include_role:
        name: gitlab_cli
</pre></code>