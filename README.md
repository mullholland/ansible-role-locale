# [locale](#locale)

|GitHub|GitLab|
|------|------|
|[![github](https://github.com/mullholland/ansible-role-locale/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-locale/actions)|[![gitlab](https://gitlab.com/mullholland/ansible-role-locale/badges/master/pipeline.svg)](https://gitlab.com/mullholland/ansible-role-locale)|[![quality](https://img.shields.io/ansible/quality/unset)](https://galaxy.ansible.com/mullholland/locale)|

description

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
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


## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
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

The machine needs to be prepared in CI this is done using `molecule/default/prepare.yml`:
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





## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

-   [debian9](https://hub.docker.com/r/mullholland/docker-molecule-debian9)
-   [debian10](https://hub.docker.com/r/mullholland/docker-molecule-debian10)
-   [debian11](https://hub.docker.com/r/mullholland/docker-molecule-debian11)
-   [ubuntu1804](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu1804)
-   [ubuntu2004](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu2004)
-   [centos7](https://hub.docker.com/r/mullholland/docker-molecule-centos7)
-   [centos-stream8](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream8)
-   [centos-stream9](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream9)
-   [ubi8](https://hub.docker.com/r/mullholland/docker-molecule-ubi8)
-   [fedora34](https://hub.docker.com/r/mullholland/docker-molecule-fedora34)
-   [fedora35](https://hub.docker.com/r/mullholland/docker-molecule-fedora35)
-   [amazonlinux](https://hub.docker.com/r/mullholland/docker-molecule-amazonlinux)
-   [rockylinux8](https://hub.docker.com/r/mullholland/docker-molecule-rockylinux8)
-   [almalinux8](https://hub.docker.com/r/mullholland/docker-molecule-almalinux8)

The minimum version of Ansible required is 2.10, tests have been done to:

-   The previous versions.
-   The current version.





If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-locale/issues)

## [License](#license)

MIT


## [Author Information](#author-information)

[Mullholland](https://github.com/mullholland)

## [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
