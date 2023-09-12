# ansible-role-prosody  [![Ansible Role](https://img.shields.io/ansible/role/d/63227)](https://galaxy.ansible.com/cornfeedhobo/prosody)

Install and configure Prosody XMPP Server.

## Table of content

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [prosody_config](#prosody_config)
  - [prosody_config_dir](#prosody_config_dir)
  - [prosody_configure](#prosody_configure)
  - [prosody_data_dir](#prosody_data_dir)
  - [prosody_group](#prosody_group)
  - [prosody_install](#prosody_install)
  - [prosody_package_state](#prosody_package_state)
  - [prosody_packages](#prosody_packages)
  - [prosody_service](#prosody_service)
  - [prosody_service_enabled](#prosody_service_enabled)
  - [prosody_service_state](#prosody_service_state)
  - [prosody_ssl](#prosody_ssl)
  - [prosody_ssl_dir](#prosody_ssl_dir)
  - [prosody_ssl_pairs](#prosody_ssl_pairs)
  - [prosody_user](#prosody_user)
  - [prosody_vhosts](#prosody_vhosts)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.1`

## Default Variables

### prosody_config

Uses encode_lua() to transform the supplied yaml-formatted config
to a corresponding lua config file.

#### Default value

```YAML
prosody_config: {}
```

#### Example usage

```YAML
external_addresses: ["1.2.3.4"]
c2s_interfaces: ["0.0.0.0"]
s2s_interfaces: ["0.0.0.0"]
http_interfaces: ["0.0.0.0"]
https_interfaces: ["0.0.0.0"]
http_external_url: "https://xmpp.example.org/"
trusted_proxies: ["127.0.0.1"]
admins: ["admin@example.org"]
network_backend: "event"
modules_enabled: [...]
contact_info:
  abuse: ["mailto:abuse@example.org", "xmpp:abuse@example.org"]
  admin: ["mailto:admin@example.org", "xmpp:admin@example.org"]
allow_registration: false
c2s_require_encryption: true
s2s_require_encryption: true
s2s_secure_auth: false
limits:
  c2s:
    rate: "10kb/s"
  s2sin:
    rate: "30kb/s"
authentication: "dovecot"
dovecot_auth_host: "127.0.0.1"
dovecot_auth_port: "864"
disable_sasl_mechanisms: ["LOGIN"]
storage: "sql"
sql:
  driver: "SQLite3"
  database: "prosody.sqlite"
default_archive_policy: "roster"
archive_expires_after: "never"
log:
  debug: "*console"
certificates: "/etc/prosody/ssl"
c2s_direct_tls_ports: [5223]
s2s_direct_tls_ports: [5270]
pidfile: "/run/prosody/prosody.pid"
```

### prosody_config_dir

#### Default value

```YAML
prosody_config_dir: '{{ __prosody_config_dir }}'
```

### prosody_configure

#### Default value

```YAML
prosody_configure: false
```

### prosody_data_dir

#### Default value

```YAML
prosody_data_dir: '{{ __prosody_data_dir }}'
```

### prosody_group

#### Default value

```YAML
prosody_group: prosody
```

### prosody_install

#### Default value

```YAML
prosody_install: false
```

### prosody_package_state

#### Default value

```YAML
prosody_package_state: present
```

### prosody_packages

#### Default value

```YAML
prosody_packages: '{{ __prosody_packages }}'
```

### prosody_service

#### Default value

```YAML
prosody_service: false
```

### prosody_service_enabled

#### Default value

```YAML
prosody_service_enabled: false
```

### prosody_service_state

#### Default value

```YAML
prosody_service_state: stopped
```

### prosody_ssl

#### Default value

```YAML
prosody_ssl: false
```

### prosody_ssl_dir

#### Default value

```YAML
prosody_ssl_dir: '{{ prosody_config_dir }}/ssl'
```

### prosody_ssl_pairs

- name: ""
key: ""
crt: ""
ca: ""

#### Default value

```YAML
prosody_ssl_pairs: []
```

#### Example usage

```YAML
- name: "example.org"
  key: "{{ lookup('file', 'example.org.key') }}"
  crt: "{{ lookup('file', 'example.org.crt') }}"
  ca: "{{ lookup('file', 'ca.crt') }}"
```

### prosody_user

#### Default value

```YAML
prosody_user: prosody
```

### prosody_vhosts

Uses a custom template to transform the supplied yaml-formatted
virtual host descriptions

#### Default value

```YAML
prosody_vhosts: {}
```

#### Example usage

```YAML
example.org: >
  Component "muc.example.org" "muc"
      name = "example.org chatrooms"
      modules_enabled = { "muc_mam", "vcard_muc" }
  Component "xup.example.org" "http_upload"
      http_upload_expire_after = 60 * 60 * 24 * 30
      http_upload_file_size_limit = 1024 * 1024 * 10
  Component "x65.example.org" "proxy65"
```

## Discovered Tags

**_prosody_**

**_prosody-configure_**

**_prosody-install_**

**_prosody-service_**

**_prosody-ssl_**


## Dependencies

None.

## License

MIT

## Author

cornfeedhobo
