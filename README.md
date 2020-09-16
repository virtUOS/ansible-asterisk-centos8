<h1 align="center">ansible-asterisk-centos8</h1>
<p>
  <img alt="Version" src="https://img.shields.io/badge/version-1.0-blue.svg?cacheSeconds=2592000" />
  <a href="https://github.com/virtUOS/ansible-asterisk-centos8/blob/main/LICENSE" target="_blank">
    <img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-yellow.svg" />
  </a>
</p>

> Ansible script for provsioning Asterisk (telephone system software) to route SIP phone numbers to BigBlueButton (freeswitch) endpoints. This script is used to serve a BigBlueButton Cluster with SIP telephony via two sipgate trunks.

## Install

1. Clone this repository
```sh
git clone URL
```

2. Edit hosts.yml
```yml
all:
  children:
    production:
      hosts:
        HOST1: # Edit host (e.g. asterisk.example.com)
```

2. Edit group_vars/all/vars.yml for main install configuration

3. Edit group_vars/all/machines.yml to setup all BigBlueButton endpoints. Generate strong secrets via:
```sh
pwgen -n1 64
```
Template (group_vars/all/machines.yml)
```yml
sip_endpoints_secrets:
  HOST1: # Edit/add new hosts (e.g. bigbluebutton.example.com)
    create_endpoint: true
    sip_phone: 491234999999 # schema 491234999999
    sip_password: SIP_PASSWORD # generate strong password
  HOST2:
    create_endpoint: true
    sip_phone: 491234888888
    sip_password: SIP_PASSWORD
  HOST3:
    create_endpoint: true
    sip_phone: 491234777777
    sip_password: SIP_PASSWORD
```

4. Generate vault password for vault.yml and machines.yml. Encrypt these files via ansible-vault
```
ansible-vault encrypt FILE
```

5. Deploy via ansible
```sh
ansible-playbook asterisk.yml
```

## Author

:computer: **virtUOS (University Osnabrück)**

* www: [virtuos.uni-osnabrueck.de](https://virtuos.uni-osnabrueck.de/)
* Github: [@virtUOS](https://github.com/virtUOS)

👤 **Florian Feyen**

* Github: [@ffeyen](https://github.com/ffeyen)

## 🤝 Contributing

Contributions, issues and feature requests are welcome!<br />Feel free to check [issues page](https://github.com/virtUOS/ansible-asterisk-centos8/issues).

## Show your support

Give a ⭐️ if this project helped you!

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
