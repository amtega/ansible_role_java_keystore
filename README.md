# Amtega java_keystore role

This is an [Ansible](http://www.ansible.com) role to manage a java keystore.

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Example Playbook

This is an example playbook:

~~~ yaml
---
- hosts: localhost
  roles:  
    - role: amtega.java_keystore
      vars:
        java_keystore_id: keystore
        java_keystore_path: /tmp/keystore.jks
        java_keystore_password: changeit

        java_keystore_keys:
          - alias: testing
            path: /tmp/mycert.crt
            state: self-signed
            extra_args:
              - -sigalg SHA256withRSA
              - -keyalg RSA
              - -dname "CN={{ inventory_hostname }}"
              - -ext "SAN=DNS:localhost"
              - -validity {{ 365 * 100 }}
~~~

## Testing

Tests are based on [molecule with docker containers](https://molecule.readthedocs.io/en/latest/installation.html).

```shell
cd amtega.java_keystore

molecule test --all
```

## License

Copyright (C) 2022 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Juan Antonio Valiño García
