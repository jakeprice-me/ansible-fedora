# Ansible Playbook to Configure Fedora 34 on ThinkPad

This playbook configures my ThinkPad T480, following a fresh installation of Fedora.

## Install Ansible

Install Ansible using `dnf`.

```sh
sudo dnf install ansible --assumeyes
```

## Ansible Galaxy Collections

Install the following collections when running on a fresh Fedora install.

```sh
ansible-galaxy collection install community.general
```

## Clone Repository

Clone the repository into `~/Downloads`.

```sh
git clone https://git.jacobprice.tech/jprice/ansible-thinkpad-fedora.git ~/Downloads/
```

## Ansible Vault

Create an Ansible Vault file, and corresponding `.vault_password` file.

`vault.yml` should contain the values for:

- `vault_samba_username`
- `vault_samba_password`

The `vault.yml` file is encrypted and passphrase protected. `.vault_password` is not committed to version control. If lost create a new `vault.yml` and enter values for the above (stored in KeePass).

```sh
# Create .vault_password:
echo $(tr --complement --delete '[:alnum:]' < /dev/urandom | fold --width=64 | head --lines=1) > .vault_password.yml

# Create vault:
ansible-vault create vault.yml

# Enter the username and password values:
vault_samba_username: <username>
vault_samba_password: <password>
```

## Ansible Config

To save specifying the vault password, `ansible.cfg` contains the path to `.vault_password`.

```ini
[defaults]
vault_password_file = .vault_password
```

## Run Playbook

Following a fresh installation of Fedora, you'll need to install Ansible first, before you can run the playbook locally.

```sh
# Install Ansible:
sudo dnf install ansible

# Run Playbook:
ansible-playbook thinkpad_fedora.yml
```
