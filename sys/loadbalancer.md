# Loadbalancer

## Keepalived

### Config files (not necessarily these)
- `/etc/sysconfig/network-scripts/ifcfg-dummy0`
- `/etc/keepalived/conf.d/keepalived_vrrp_{INSTANCE}.conf`

### Keepalived and basic commands to test it
https://www.redhat.com/sysadmin/keepalived-basics

### Check keepalived communications
```sh
tcpdump proto 112
```

### Check status of dummy0 interface
```sh
ip addr show dummy0
# 10: dummy0: <BROADCAST,NOARP> mtu 1500 qdisc noop state DOWN group default qlen 1000
#    link/ether b2:74:5d:97:c6:b7 brd ff:ff:ff:ff:ff:ff
```

### Get the peer of the LB
```sh
sudo cat /etc/keepalived/conf.d/keepalived_vrrp_instance__VI_* | grep -A 2 -i "unicast_peer"
```
