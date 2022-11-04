# poet-role

Role to manage a cloud instance

## Requirements:

- ansible-galaxy collection install --force devsec.hardening

### Default variables

- `ansible_ssh_user` - default: `{{ managing_user }}`
- `email_sender` - default: `{{ admin_email }}`

### Environment variables

- `ansible_become_password` - env `POET_CLOUD_BECOME_PASS`
- `password_salt` - env `POET_CLOUD_PASSWORD_SALT`
- `managing_user_password` - env `POET_CLOUD_MANAGING_USER_PASS`
- `admin_email` - env `POET_DJANGO_ADMIN_EMAIL`

### Other variables

- `managing_user`

## tags

- **new_instance**: Creates a new hardened Debian instance
- **compact**: Installs Postgresql, Nginx as reverse proxy to Django
  - Extra vars:
    - Postgresql
      `django_postgres_user`
      `django_postgres_user_pass`
    - Nginx:
      `server_domain_name`
      `server_alias_domain_name` [optional]
    - Certbot
      `domains` (comma separated, the first, is main domain)
