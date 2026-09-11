# Security Investigation

## 1. Investigation Overview

This investigation evaluates network connectivity and security controls between an attacker environment and a target environment deployed in separate Docker networks.

The objective is to determine whether network segmentation, routing, and firewall policies effectively restrict communication between the two environments.

---

## 2. Lab Environment

### Attacker

* Container: `scripting-lab`
* IP Address: `10.10.10.10`
* Network: `attacker-net`
* Subnet: `10.10.10.0/24`

### Target

* Container: `target-lab`
* IP Address: `10.10.20.10`
* Network: `target-net`
* Subnet: `10.10.20.0/24`

### Firewall

* Platform: pfSense
* Version: 2.7.2
* LAN Interface: `192.168.50.1`

---

## 3. Security Scenario

The attacker container attempts to communicate with a target container located in a separate network segment.

The investigation focuses on:

* Network isolation
* Routing behavior
* TCP connectivity
* Firewall enforcement
* Security policy validation

---

## 4. Connectivity Testing

The following tests were performed from the attacker environment.

### ICMP Test

```bash
ping 10.10.20.10
```

Purpose:

To determine whether the attacker can reach the target at the network layer.

### TCP Connectivity Test

```bash
nc -zv 10.10.20.10 <PORT>
```

Purpose:

To determine whether a specific TCP service is reachable from the attacker environment.

### Port Scanning

```bash
nmap 10.10.20.10
```

Purpose:

To identify reachable services on the target system during the controlled lab test.

---

## 5. Observations

The attacker and target containers are deployed in separate Docker networks.

Connectivity results were analyzed to determine whether traffic was:

1. Successfully routed to the target.
2. Rejected by the destination service.
3. Dropped because of network isolation.
4. Blocked by a firewall policy.

A failed connection alone does not prove that pfSense blocked the traffic.

Firewall enforcement must be validated using routing information, firewall logs, and the configured firewall rules.

---

## 6. Firewall Analysis

The pfSense configuration was reviewed to identify policies controlling traffic between network segments.

The investigation checks:

* Source network
* Destination network
* Destination port
* Protocol
* Firewall action
* Firewall logs

If the traffic is confirmed in the pfSense logs and the corresponding rule shows a block action, the result can be classified as firewall-enforced filtering.

If the traffic does not reach pfSense, the result should instead be classified as network isolation or routing limitation.

---

## 7. Evidence

The following evidence is collected as part of the investigation:

* Docker network configuration
* Container IP addresses
* Connectivity test results
* pfSense firewall rules
* pfSense firewall logs
* Network architecture diagram

Screenshots are stored in the `screenshots/` directory.

---

## 8. Security Assessment

The lab demonstrates the importance of separating network connectivity from firewall enforcement.

Network segmentation can reduce the attack surface by preventing direct communication between isolated environments.

Firewall policies provide an additional security layer when traffic is routed through the firewall and evaluated against defined rules.

---

## 9. Conclusion

The investigation demonstrates how network segmentation, routing, and firewall policies can be analyzed in a controlled cybersecurity lab.

The results are documented using configuration evidence, connectivity testing, and firewall analysis rather than relying only on connection failures.

This approach provides a more accurate method for validating network security controls.
