# Target Container

## Role

Target system used to test connectivity, SSH exposure, segmentation,
and resource hardening.

## Container

Name:
target-lab

Image:
ubuntu:24.04

## Segmented Network

target-net

Subnet:
10.10.20.0/24

Container IP:
10.10.20.10

Docker Gateway:
10.10.20.1

## Exposed Service

SSH
TCP/22

## Resource Limits

Memory:
256 MB

CPU:
0.5 CPU

## Security Purpose

- Controlled lateral movement testing
- Network segmentation testing
- SSH exposure analysis
- Resource exhaustion mitigation
