
### Phase 1 — Shared Docker Network

Network:
cyberlab

Subnet:
172.18.0.0/16

Gateway:
172.18.0.1

Containers:

Attacker:
scripting-lab
Image: python:3.12-slim

Target:
target-lab
Image: ubuntu:24.04

Results:
- Docker DNS resolution worked.
- TCP/22 SSH was reachable.
- Controlled SSH lateral movement was demonstrated.
- TCP/80 returned connection refused because no service was listening.









### Phase 2 — Network Segmentation

Attacker Network:
attacker-net
10.10.10.0/24

Attacker:
10.10.10.10

Target Network:
target-net
10.10.20.0/24

Target:
10.10.20.10

Result:
Direct attacker-to-target connectivity failed.

Interpretation:
Network isolation / incomplete routing was demonstrated.














