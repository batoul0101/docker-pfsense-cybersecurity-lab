# Attacker Container

## Role

Source / attacker simulation container used to generate controlled
network traffic against the target environment.

## Container

Name:
scripting-lab

Image:
python:3.12-slim

## Initial Network

cyberlab

## Segmented Network

attacker-net

Subnet:
10.10.10.0/24

Container IP:
10.10.10.10

Docker Gateway:
10.10.10.1

## Purpose

- Generate ICMP tests
- Generate TCP connectivity tests
- Test SSH connectivity
- Demonstrate controlled lateral movement
- Test network segmentation
- Support future firewall validation
