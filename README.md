# Ansible Playbook for Fedora 35

This playbook configures my personal devices following a fresh installation of my go-to distro, Fedora.

## Install Ansible

Install Ansible using `dnf`.

```sh
sudo dnf install ansible --assumeyes
```

## Clone Repository

Clone the repository into `~/Downloads`.

```sh
git clone https://github.com/jakeprice-dev/ansible-fedora ~/Downloads/ansible-fedora
```

## Ansible Variables

Create a `vars.yml` file in the repository folder, and provide values for the below variables.

```yaml
code_root: <value>
docs_root: <value>
firefox_start_page: <value>
git_config_user_email: <value>
git_config_user_name: <value>
healthcheck_unison: <value>
personal_username: <value>
unison_script: <value>
```

## Ansible Collections

Whilst you are still within the repository directory, install the collections specified in `requirements.yml`.

```sh
ansible-galaxy collection install -r requirements.yml
```

## Directories

The playbook depends on a few directories and files being in place already. 

- `~/my/files/documents/vault`

Then clone the following GitHub repositories into the directories below.

- https://github.com/jakeprice-dev/dotfiles.git into `my/files/code/dotfiles`
- https://github.com/jakeprice-dev/espanso-config.git into `my/files/code/espanso-config`
- https://github.com/jakeprice-dev/misc-config.git into `my/files/code/misc-config`

## Run Playbook

Run the playbook to configure the new installation of Fedora, and input your `sudo` password when prompted.

```sh
# Run Playbook:
ansible-playbook --ask-become-pass --extra-vars "hostname=<enter_hostname>" playbook.yml
```

