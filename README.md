# Ansible Playbook to Configure Fedora 34 on ThinkPad

This playbook configures my ThinkPad T480, following a fresh installation of my goto distro, Fedora.

## Install Ansible

Install Ansible using `dnf`.

```sh
sudo dnf install ansible --assumeyes
```

## Clone Repository

Clone the repository into `~/Downloads`.

```sh
git clone https://git.jpr.sh/jprice/ansible-thinkpad-fedora.git ~/Downloads/ansible-thinkpad-fedora
```

## Ansible Variables

Create a `vars.yml` file in the repository folder, and provide values for the below variables.

```yaml
firefox_start_page: <value>
git_config_user_email: <value>
git_config_user_name: <value>
personal_username: <value>
```

## Ansible Collections

Still within the repository directory, install the collections specified in `requirements.yml`.

```sh
ansible-galaxy collection install -r requirements.yml
```

## Run Playbook

Run the playbook to configure the new installation of Fedora, and input your `sudo` password when prompted.

```sh
# Run Playbook:
ansible-playbook --ask-become-pass playbook.yml
```

