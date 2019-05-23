Ansible Homebridge
==================

Ansible role to configure [Homebridge].
I recommend [geerlingguy.nodejs][nodejs] to install and configure NodeJS before.

Example playbook:

```
- hosts: pi
  become: true

  roles:
    - role: nodejs
      tags:
        - nodejs
    - role: homebridge
      tags:
        - homebridge

  vars:
    nodejs_npm_global_packages:
      - homebridge
      - homebridge-hue
    npm_config_unsafe_perm: "true"
    homebridge_username: "CC:22:3D:AA:AA:AA"
    homebridge_port: 51826
    homebridge_pin: "030-45-153"

    homebridge_platforms:
      - platform: Hue
        lights: true
        host: hue.lan
        nupnp: false

    homebridge_accessories:
      - accessory: Sonos
        name: Sonos Kitchen
        room: Kitchen
        mute: false
```

[Homebridge]: https://github.com/nfarina/homebridge
[nodejs]: https://galaxy.ansible.com/geerlingguy/nodejs
