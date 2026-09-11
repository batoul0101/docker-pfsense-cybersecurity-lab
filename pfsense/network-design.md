# pfSense Network Design

## pfSense Platform

pfSense 2.7.2-RELEASE

## Deployment

pfSense runs as a virtual machine.

Hypervisor:
Hyper-V

## Interfaces

| Interface | Network | IP Address |
|---|---|---|
| WAN | WAN-LAB | 192.168.1.108/24 |
| LAN | LAN-LAB-PFSENSE | 192.168.50.1/24 |

## Windows LAN Interface

192.168.50.100

## Intended Role

pfSense is intended to become the routing and firewall enforcement
point between the attacker and target networks.
