# poet-role

Role to manage a cloud instance

## Requirements:

- ansible-galaxy collection install --force devsec.hardening

### Default variables

- `ansible_ssh_user` - default: `{{ managing_user }}`
- `email_sender` - default: `{{ admin_email }}`

### Necessary variables

- `ansible_become_password`
- `password_salt`
- `managing_user_password`
- `admin_email`
- `managing_user`

## tags

- **new_instance**: Creates a new hardened Debian instance
- **compact**: Installs Postgresql, Nginx as reverse proxy to Django

  - Extra vars:

    - Postgresql

      - `django_postgres_user`
      - `django_postgres_user_pass`

    - Nginx:

      - `server_domain_name`
      - `django_admin_path`
      - `server_alias_domain_name` [optional]
      - nginx_compact:
        - `POET_PROJECT` (Environment Variable)

    - Certbot

      - `domains` (comma separated, the first, is main domain)

    - Upstream Maintenance
      - `ANSIBLE_DOTENV_FILE_PATH` (Environment Variable)
      - `POET_PROJECT_PATH` (Environment Variable)
      - `ANSIBLE_LOCAL_PROJECT_PATH` (Environment Variable)
