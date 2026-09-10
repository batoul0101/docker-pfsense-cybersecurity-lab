Internet / WAN
      |
   WAN-LAB
      |
   pfSense VM
WAN: 192.168.1.108
LAN: 192.168.50.1
      |
LAN-LAB-PFSENSE
      |
 Docker / Host
   /       \
  /         \
Attacker    Target
Network     Network
10.10.10.0  10.10.20.0
   |           |
10.10.10.10  10.10.20.10



## Current Architecture Limitation

The Docker networks currently use Docker-managed gateways:

- attacker-net gateway: 10.10.10.1
- target-net gateway: 10.10.20.1

Because these gateways are managed by Docker, attacker-to-target
traffic has not yet been confirmed to traverse pfSense.
