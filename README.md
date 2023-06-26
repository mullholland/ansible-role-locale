# [locale](#locale)

Configures the local locale settings.

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-locale/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-locale/actions)|[![gitlab](https://gitlab.com/opensourceunicorn/ansible-role-locale/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-locale)|[![quality](https://img.shields.io/ansible/quality/57673)](https://galaxy.ansible.com/mullholland/locale)|[![downloads](https://img.shields.io/ansible/role/d/57673)](https://galaxy.ansible.com/mullholland/locale)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-locale.svg)](https://github.com/mullholland/ansible-role-locale/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-locale/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "mullholland.locale"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-locale/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  tasks:
    - name: Debian/Ubuntu | Install cron for Backupscript
      ansible.builtin.apt:
        name:
          - "cron"
        state: latest
        update_cache: true
      when: ansible_os_family == "Debian"

    - name: RedHat/CentOS | Install cron for Backupscript
      ansible.builtin.package:
        name:
          - "cronie"
        state: latest
      when: ansible_os_family == "RedHat" or ansible_os_family == "Rocky"
```


## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-locale/blob/master/defaults/main.yml):

```yaml
---
# get current locale `locale`
# get possible options with `locale -a`
locale_lang: en_US.UTF-8

# change only if you know what you are doing
locale_language: "{{ locale_lang }}"
locale_lc_address: "{{ locale_lang }}"
locale_lc_all: "{{ locale_lang }}"
locale_lc_collate: "{{ locale_lang }}"
locale_lc_ctype: "{{ locale_lang }}"
locale_lc_identification: "{{ locale_lang }}"
locale_lc_measurement: "{{ locale_lang }}"
locale_lc_messages: "{{ locale_lang }}"
locale_lc_monetary: "{{ locale_lang }}"
locale_lc_name: "{{ locale_lang }}"
locale_lc_numeric: "{{ locale_lang }}"
locale_lc_paper: "{{ locale_lang }}"
locale_lc_response: "{{ locale_lang }}"
locale_lc_telephone: "{{ locale_lang }}"
locale_lc_time: "{{ locale_lang }}"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-locale/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-locale/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/mullholland/docker-centos-systemd/general)|all|
|[Amazon](https://hub.docker.com/repository/docker/mullholland/docker-amazonlinux-systemd/general)|Candidate|
|[Fedora](https://hub.docker.com/repository/docker/mullholland/docker-fedora-systemd/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/mullholland/docker-ubuntu-systemd/general)|all|
|[Debian](https://hub.docker.com/repository/docker/mullholland/docker-debian-systemd/general)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-locale/issues)

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-locale/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)

Please consider [sponsoring me](https://github.com/sponsors/mullholland).
