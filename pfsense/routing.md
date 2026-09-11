# Routing Design

## Objective

Route traffic between:

10.10.10.0/24
and
10.10.20.0/24

through pfSense.

## Current State

Attacker:
10.10.10.10

Default Gateway:
10.10.10.1

Target:
10.10.20.10

Default Gateway:
10.10.20.1

Both gateways are currently Docker-managed.

## Current Limitation

The routing path between attacker and target has not yet been completed
through pfSense.

## Required Future State

Attacker
↓
pfSense
↓
Target

and return traffic:

Target
↓
pfSense
↓
Attacker

## Verification Requirement

Both forward and return routing paths must be verified before firewall
policy enforcement can be accurately tested.
