# My lightweight IoT Firewall Project

## Introduction

Many of us today have dedicated IoT SSIDs to separate IoT devices from internal networks. The problems arise when systems like HomeAssistant need to communicate with these IoT devices, and we need network separation which can 

In addition, it's important where possible to limit the outbound internet access of IoT devices. This is because whilst internet access can be important for some IoT functionality and over-the-air updates, a compromised IoT device could be used for data exfiltration and botnet infection.

## The solution

The solution I have devised for this is a containerized IoT Firewall which does the following:

   * Integrates with netbox to associate MAC addresses with devices for DHCP and tag profiles for firewall rules
   * Default iptables filtering of any IoT to internal network traffic unless an exception existd
   * DNS-based outbound internet access for IoT devices to allow limited communication with cloud-based services
