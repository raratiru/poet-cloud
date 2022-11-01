# poet-role
Role to manage a cloud instance

## Requirements:
  * ansible-galaxy collection install --force devsec.hardening

## Default variables
  * `managing_user` - default: `claudia`
  * `ansible_ssh_user` - default: `{{ managing_user }}`

## Environment variables
  * `ansible_become_password` - env `POET_CLOUD_BECOME_PASS`
  * `password_salt` - env `POET_CLOUD_PASSWORD_SALT`
  * `managing_user_password` - env `POET_CLOUD_MANAGING_USER_PASS`

tags
----

* **new_instance**: Creates a new hardened Debian instance