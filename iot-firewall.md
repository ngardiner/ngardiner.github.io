# My lightweight IoT Firewall Project

## Introduction

Many of us today have dedicated IoT SSIDs to separate IoT devices from internal networks. The problems arise when systems like HomeAssistant need to communicate with these IoT devices, and we need network separation which can 

In addition, it's important where possible to limit the outbound internet access of IoT devices. This is because whilst internet access can be important for some IoT functionality and over-the-air updates, a compromised IoT device could be used for data exfiltration and botnet infection.

## The solution

The solution I have devised for this is a containerized IoT Firewall which does the following:

   * Allows for HA configuration in limited active-standby mode (ie. active-standby on a per-interface/VLAN level, meaning you could have multiple active-active instances if you have segmented your IoT network(s) appropriately.
   * Integrates with netbox to associate MAC addresses with devices for DHCP and tag profiles for firewall rules
   * Default iptables filtering of any IoT to internal network traffic unless an exception existd
   * DNS-based outbound internet access for IoT devices to allow limited communication with cloud-based services

## Installing

To deploy your own [iot-firewall](https://github.com/ngardiner/iot-firewall) system, follow the steps below:

   * Create at least 1 (and as many as 8, but this would be excessive due to the active-standby nature of the Firewall) Linux containers. Both RedHat and Ubuntu distributions are supported.
   * Install the following packages, depending on which of these distributions you are using:
      * Debian / Ubuntu
      * RedHat / CentOS
