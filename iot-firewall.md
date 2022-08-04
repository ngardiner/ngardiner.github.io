# My lightweight IoT Firewall Project

## Introduction

Many of us today have dedicated IoT SSIDs to separate IoT devices from internal networks. The problems arise when systems like HomeAssistant need to communicate with these IoT devices, and we need network separation which can 

In addition, it's important where possible to limit the outbound internet access of IoT devices. This is because whilst internet access can be important for some IoT functionality and over-the-air updates, a compromised IoT device could be used for data exfiltration and botnet infection.

### Why customize?

I chose to customize this system for my use because container-friendly IP Firewall deployments are particularly hard to come by, and given all the necessary components are available within lightweight LXC containers today, I couldn't understand why I'd need to sacrifice the efficiency of containers for a VM to implement this solution.

## The solution

The solution I have devised for this is a containerized IoT Firewall which does the following:

   * Allows for HA configuration in limited active-standby mode (ie. active-standby on a per-interface/VLAN level, meaning you could have multiple active-active instances if you have segmented your IoT network(s) appropriately.
      * Multi active-standby routing can be implemented either using tracking VIPs or BGP
   * Integrates with netbox to associate MAC addresses with devices for DHCP and tag profiles for firewall rules
   * Default iptables filtering of any IoT to internal network traffic unless an exception existd
   * DNS-based outbound internet access for IoT devices to allow limited communication with cloud-based services

## Installing

To deploy your own [iot-firewall](https://github.com/ngardiner/iot-firewall) system, follow the steps below:

   * Create at least 1 (and as many as 8, but this would be excessive due to the active-standby nature of the Firewall) Linux containers. Both RedHat and Ubuntu distributions are supported.
      * A privileged LXC container is not required for this project
      * You will need to configure one interface per IoT network, with a per-node IP address and a VIP IP for IoT devices to use.
      * Even for single node deployments, you need to use per-node and VIP addressing to allow it to be converted to HA in the future.
      * 1 vCPU, 512M RAM are sufficient for most installations, if your container platform (eg Proxmox) allows resource constraint configuration.
   * Install the following packages, depending on which of these distributions you are using:
      * Debian / Ubuntu

``` apt install -y corosync pacemaker pcs ulogd2 ```

      * RedHat / CentOS
   * Pull the iot-firewall repository

``` git pull https://github.com/ngardiner/iot-firewall ```

## Todo

Some of the things I'd like to add to this platform in the future:

   * Blocklist for poor IP reputation
   * DNS-based malware detection using a DNS forwarder proxy
   * Quarantining / Penalty Box for devices which are exhibiting poor behaviour
