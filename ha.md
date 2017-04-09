# Home Automation

## Introduction

Home Automation is an exciting new area of technology for anyone with an interest in integrating modern technology and scripting into our daily life.

For anyone with scripting and automation background, it provides a way to outsource things we would typically manage manually to smart processes which are able to read and react to many dynamic values from dynamic sensors around our home.

## System Architecture

The System Architecture for my Home Automation system comes down to a mix of networking, compute and storage resources used with excellent modern Home Automation (or IoT) devices. 

### Structure

Within the house, there are 3 locations where the equipment used to support the HA environment are hosted. These are in hidden/out of sight locations in 3 areas of the house known as the North, Central and South zones. It is important to distribute the equipment into these different zones as much of the solution relies on wireless technologies including WiFi and Zigbee

In each location, there are 3 components. The first is one or more switches, connected to each of the other zones by LACP bundled ethernet interfaces. The second is a small server such as an Intel NUC i5 for Proxmox. The third is a set of disks connected to the server which are used for Ceph storage.

## Components

### Network Switching and Routing

Our Home Automation switching and routing platform provides a network backbone of up to 6Gbps, 

### Virtualization Platform

For virtualization of systems and services at home, I have deployed the [Proxmox VE](https://www.proxmox.com) environment. Proxmox VE provides KVM-based virtualization and LXC-based Linux Containers

For a NUC machine, we have 3 types of storage - a 2.5 inch slot yupically, as well as flash storage for ISO images, backups and template files. 

### Distributed Storage

Distributed Storage is provided through Ceph 

### Home Automation Components

#### Cameras

Cameras are

6 outdoor cameras ($313) and 4 indoor cameras ($185) 

#### Lighting

For indoor LED lighting, I am using Xiaomi Yeelight RGB bulbs. Yeelights use WiFi for communication, which has a slightly higher level of complexity and power utilization than a hub based solution such as the Philips Hue system, but provides a high level of independence to avoid situations where lighting is impacted by a single hub failure (leveraging the inherent WiFi redundancy that was established in the earlier design) and 

#### Temperature and Humidity Sensors

For measuring Temperature and Humidity, I have 5 Xiaomi sensors (AU$75) which provide real-time feedback through the Xiaomi Home Hub over the Zigbee wireless protocol. 3 of those sensors are located within the 3 network equipment locations in the house (North, Central, South) and assist in monitoring the equipment to ensure it is not overheating.

The remaining two Temperature and Humidity sensors are wall-mounted indoors, at either side of the house. These are used to monitor the indoor temperature to determine when 

#### Whole-house Audio

In order to provide whole-house audio, I picked up 6 NEXX WT3050 devices which provide 2 x 100Mbps ethernet ports, 1 USB port and 54Mbps WiFi. The NEXX devices are able to run OpenWRT, which provides great flexibility in configuring 

<center>
  <img src="images/IMG_20170409_175646.jpg" />
  <br /><i>The 6 NEXX WT3050 devices used to provide whole-house audio</i>
</center>

For $29.75, I picked up 6 sets of USB A to DC jack connectors, as well as 6 sets of DC jack to USB micro connectors, and 6 USB audio sound card devices. These are coupled with 6 passive PoE injectors (for $20.80), to allow the NEXX devices to be powered via Ethernet cables.

To connect the USB audio devices to the NEXX devices, I purchased 6 rotatable 3-port USB hubs, at a cost of $23.67. These USB hubs allow multiple devices to be connected to each of the NEXX devices, in a small form factor, providing 

<center>
  <img src="images/IMG_20170409_163837.jpg" />
</center>
