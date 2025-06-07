# manual-fan.service

## Description

An IPMI systemd service too and some useful commands. This service with use IPMI commands to ensure manual control of fans is enabled. It will also turn off the forced PCIe filled fan to high feature. A Dell PowerEdge r730xd does not seem to offer any fan normal fan control outside or Windows Server OS.

## Installation

To install and use:

1. Add `manual-fan.service` to `/etc/systemd/system/`
2. `systemctl daemon reload`
3. `systemctl enable manual-fan.service`
4. `systemctl start manual-fan.service`

The goal is to use this service in conjunction with another service to control the system fans.

## Useful Notes

Install ipmi: `sudo apt install ipmitool`
List fans: `sudo ipmitool list | grep Fan`
Sets all the system fans to lower %: `sudo /us/bin/imitool raw 0x30 0x30 ox02 Oxff Oxb`