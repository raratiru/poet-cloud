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
      - `nginx_cache_keys_zone_size` [default: 10m]
      - `nginx_cache_max_size` [default: 20g]
      - `nginx_cache_inactive_time` [default: 180m]
      - `nginx_use_proxy_cache` [defined & boolean]
      - `nginx_cache_background_update` [defined & boolean]
      - `nginx_cache_revalidate_with_conditional_headers` [defined & boolean]
      - `nginx_proxy_server_port` [default: 8001]
      - nginx_website_conf:
        - `POET_PROJECT` (Environment Variable)
        - `POET_CLOUD_SERVER_DOMAIN_NAME` (Environment Variable)

    - Certbot

      - `domains` (comma separated, the first, is main domain)
    - Upstream Initialization
      - `POET_PROJECT` (Environment Variable)
      - `POET_CLOUD_SERVER_DOMAIN_NAME` (Environment Variable)

    - Upstream Maintenance
      - `ANSIBLE_DOTENV_FILE_PATH` (Environment Variable)
      - `POET_PROJECT_PATH` (Environment Variable)
      - `ANSIBLE_LOCAL_PROJECT_PATH` (Environment Variable)
