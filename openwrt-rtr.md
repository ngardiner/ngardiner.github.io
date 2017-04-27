
# OpenWRT Router Configuration

## Redundancy

### keepalived

keepalived is a very useful component for providing High Availability services to the network.

Create ```/etc/hotplug.d/net/20-keepalived``` and add the following contents:

```
#!/bin/sh

/etc/init.d/keepalived restart
```
