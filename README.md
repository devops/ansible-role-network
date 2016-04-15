# Ansible Role: network

This roles enables users to configure various network components  in their servers. The role can be used to configure

-  Ethernet Interfaces

-  Bridge Interfaces

-  Bonding interfaces


## Requirements

none

## Role Variables


`defaults/main.yml:`

```
network_ethernet_interfaces: []                #The list of ethernet interfaces to be added to the sytem
network_bond_interfaces: []                    #The list of bond interfaces to be added to the sytem
```

Note: The values for the list are listed in the `test.yml`.

## Examples

All the above examples show how to configure a single host, The below example shows how to define your network configurations
for all your machines.

- Assuming your Inventory looks as follows:

```
/etc/ansible/hosts

[servers]
servers01
servers02

```

- Describe your network configuration for each host in hostvars

```
host_vars/servers01
-------------------


network_ether_interfaces:
       - device: eth1
         bootproto: static
         address: 192.168.10.18
         netmask: 255.255.255.0
         gateway: 192.168.10.1

network_bond_interfaces:
        - device: bond0
          bootproto: dhcp
          bond_mode: 4
          bond_miimon: 100
          bond_slaves: [eth2, eth3]


host_vars/servers02
-------------------

network_ether_interfaces:
       - device: eth0
         bootproto: static
         address: 192.168.10.19
         netmask: 255.255.255.0
         gateway: 192.168.10.1

```

## Example Playbook

see `test.yml`

## Author Information

z
