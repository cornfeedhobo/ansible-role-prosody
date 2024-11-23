# ansible-role-prosody  [![Ansible Role](https://img.shields.io/ansible/role/d/cornfeedhobo/prosody)](https://galaxy.ansible.com/cornfeedhobo/prosody)

Install and configure Prosody XMPP Server.

## Table of content

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [prosody_bin_path](#prosody_bin_path)
  - [prosody_config](#prosody_config)
  - [prosody_config_dir](#prosody_config_dir)
  - [prosody_configure](#prosody_configure)
  - [prosody_group](#prosody_group)
  - [prosody_install](#prosody_install)
  - [prosody_owner](#prosody_owner)
  - [prosody_package_state](#prosody_package_state)
  - [prosody_packages](#prosody_packages)
  - [prosody_service](#prosody_service)
  - [prosody_service_enabled](#prosody_service_enabled)
  - [prosody_service_name](#prosody_service_name)
  - [prosody_service_state](#prosody_service_state)
  - [prosody_ssl](#prosody_ssl)
  - [prosody_ssl_dir](#prosody_ssl_dir)
  - [prosody_ssl_pairs](#prosody_ssl_pairs)
  - [prosody_vhosts](#prosody_vhosts)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.9`

## Default Variables

### prosody_bin_path

#### Default value

```YAML
prosody_bin_path: /usr/bin/prosody
```

### prosody_config

Uses encode_lua() to transform the supplied yaml-formatted config
to a corresponding lua config file.

#### Default value

```YAML
prosody_config: {}
```

#### Example usage

```YAML
|
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

### prosody_owner

#### Default value

```YAML
prosody_owner: prosody
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

### prosody_service_name

#### Default value

```YAML
prosody_service_name: prosody
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

#### Default value

```YAML
prosody_ssl_pairs: []
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
example.org: |
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

- cornfeedhobo.epel
- jtyr.config_encoder_filters

## License

MIT

## Author

cornfeedhobo
