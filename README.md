# Capture Detailed Network Information using Ansible

The attached playbook acts as a single command for collecting detailed network
information. When executed it collects the following command from the mentioned
Network Oses

| Network OS     | Command   |
|----------------|---------- |
| Cisco Nexus OS |show tech  |
| Cisco IOS      |show tech  |
| Arista EOS     |show tech  |
| JunOS          |request support information |


This playbook does not require an inventory and captures the detailed network
information from only a single device.

## User Input (Extra Variables)

* ``swname``: switch hostname or IP
* ``user``: user to log into network device
* ``passwd``: password to log into the network device
* ``os_type``: can be either 'nxos', 'eos', 'junos' or 'ios'
* ``tftpserver``: TFTP server hostname and IP


## TFTP Output

The file is stored with the following name:

``showtech_{{ swname }}_{{ timestamp}}.txt``

Example:

``showtech_sw01_2018-02-14T03:30:49Z.txt``

## Example Playbook Execution

This repository provides 2 examples. One to connect to a NxOS device and the
other to an IOS device.

> NOTE: these examples change the ``show_tech_command`` variable to capture
> simple command for demo purposes. By default the show tech command is properly
> configured per the OS type.

Example 1: NxOS

```
ansible-playbook capture-playbook.yml -e @test_nxos_vars.yml
```

License
-------

MIT
