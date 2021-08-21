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
git clone https://git.jacobprice.tech/jprice/ansible-thinkpad-fedora.git ~/Downloads/ansible-thinkpad-fedora
```

## Ansible Vault

To save specifying the password when you create or edit the vault, or, run the playbook, `ansible.cfg` contains the path to `.vault_password`.

```ini
[defaults]
vault_password_file = .vault_password
```

`vault.yml` must contain the below variables and their values.

```yml
vault_samba_username: <username>
vault_samba_password: <password>
```

The values can be retrieved from the `vault.kdbx` KeePass database.

Create the `ansible-vault` file, and the corresponding `.vault_password` file.

```sh
# Change to repository directory:
cd ~/Downloads/ansible-thinkpad-fedora

# Create .vault_password:
echo $(tr --complement --delete '[:alnum:]' < /dev/urandom | fold --width=64 | head --lines=1) > .vault_password

# Create vault:
ansible-vault create vault.yml

# Enter the username and password values:
vault_samba_username: <username>
vault_samba_password: <password>
```

## Run Playbook

Run the playbook to configure the new installation of Fedora.

```sh
# Run Playbook:
ansible-playbook playbook.yml
```
