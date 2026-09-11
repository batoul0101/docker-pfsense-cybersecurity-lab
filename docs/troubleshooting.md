# Troubleshooting

## Problem 1

Docker command was executed inside a container.

Resolution:

Run Docker management commands from the Docker host using PowerShell.

---

## Problem 2

TCP/80 returned connection refused.

Resolution:

The destination host was reachable but no service was listening on port 80.

---

## Problem 3

Attacker could not reach target across segmented networks.

Resolution:

The environment demonstrated network isolation and routing requires further validation through pfSense.
