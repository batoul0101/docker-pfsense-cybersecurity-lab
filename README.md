# Docker + pfSense Cybersecurity Network Segmentation Lab

## Overview

This project demonstrates how network segmentation can be implemented using Docker networks and pfSense firewall concepts.

The lab simulates an attacker environment and a target environment, separates them into different security zones, and analyzes connectivity, routing, and firewall behavior.

## Objectives

- Build attacker and target containers
- Implement network segmentation
- Explore routing concepts
- Introduce pfSense as a firewall layer
- Perform connectivity testing
- Apply container resource hardening
- Document findings and troubleshooting

## Lab Environment

| Component | Details |
|------------|---------|
| Firewall | pfSense 2.7.2 |
| Attacker | Python 3.12 Container |
| Target | Ubuntu 24.04 Container |
| Platform | Docker Desktop |
| Host OS | Windows |

## Network Design

Attacker Network: 10.10.10.0/24

Target Network: 10.10.20.0/24

Attacker Container: 10.10.10.10

Target Container: 10.10.20.10

pfSense LAN: 192.168.50.1

## Security Controls

- Network Segmentation
- Firewall Policy Design
- SSH Access Control
- Resource Hardening
- Defense in Depth

## Screenshots

### Docker Networks

![Docker Networks](screenshots/docker-networks.png)

### Containers

![Containers](screenshots/containers.png)

### pfSense Firewall Rule

![pfSense Rule](screenshots/pfsense-rule.png)

### Segmentation Test

![Segmentation Test](screenshots/segmentation-test.png)

## Key Findings

- Segmentation successfully isolated attacker and target networks.
- Routing and firewalling are separate security functions.
- Connectivity testing requires evidence-based validation.
- Resource limits provide an additional security control layer.

## Repository Structure

```text
docs/
diagrams/
screenshots/
```

## Future Enhancements

- Complete routed traffic through pfSense
- Validate firewall enforcement using logs
- Add monitoring and alerting
- Integrate SOC-focused visibility
