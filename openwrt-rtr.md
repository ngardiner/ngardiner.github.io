
# OpenWRT Router Configuration

## Redundancy

### Dynamic Routing

Using Dynamic Routing, we can synchronise routes across all of the routers. This allows the decentralized routing that we are using on the network. To do this, we are using OSPF and 

The OSPF configuration we use consists of two OSPF areas. One is the LAN OSPF area, the other is the backbone OSPF area. This allows us to maintain an LSDB (link state database) within the LAN area, which we then summarise as a network summary to the default area, which can then join to other networks such as remote LAN networks over VPN.

```
router ospf
 network 192.168.1.0/24 area 0.0.0.0
 network 10.0.0.0/8 area 0.0.0.10
 area 0.0.0.10 range 10.0.0.0/8
```

### keepalived

keepalived is a very useful component for providing High Availability services to the network.

Create ```/etc/hotplug.d/net/20-keepalived``` and add the following contents:

```
#!/bin/sh

/etc/init.d/keepalived restart
```
