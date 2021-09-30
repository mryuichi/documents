# Fujitsu - TPAC2021 Online Testfest

Fujitsu offers two services:
- Sensor unit (temperature, humidity, and airpressure)
- Proxy server

The folloing is the network configuration.
<img src="fujitsu_network.png" width=50%>

The proxy server is on the border between the VPN and Fujitsu local network and has 2 IP addresses for both of them.
On the other hand, the sensor unit is on the local network and cannot be accessed directly from the VPN. 
In this setting, the shadow device of the sensor unit has been created on the proxy server, and then
applications on the VPN can reach to the sensor unit indirectly through the endpoint that the shadow device opens.

## discovery

The proxy server and the sensor unit support mDNS to allow discovery within the same network.
The contents you can get through mDNS are as follows:
   
```
% avahi-browse -r _wot._tcp
+ eth0 IPv4 fjsensor-esp32                                _wot._tcp            local
= eth0 IPv4 fjsensor-esp32                                _wot._tcp            local
   hostname = [fjsensor-esp32.local]
   address = [192.168.0.18]
   port = [80]
   txt = ["type=Thing" "td=/.well-known/wot-thing-description"]
```

The sensor unit can be queried by the service "wot" and protocol "tcp", and 
the Thing Description can be retrieved from URL described in txt. 

```
% avahi-browse -r _wot._tcp
+ vpn_vpn IPv4 wot-proxy                                  _wot._tcp            local
= vpn_vpn IPv4 wot-proxy                                  _wot._tcp            local
   hostname = [ip-192-168-30-134-ec2-internal.local]
   address = [192.168.30.134]
   port = [80]
   txt = ["register=/Things" "retrieve=/Things"]
```

The proxy server can be queried by the name "wot-proxy". The txt field indicates 
the URLs for the interface to create a shadow device (register) and the other interface to get 
the Thing Descriptions of the shadow devices already existed (retrive).

The sensor unit for this plugfest can search the proxy server in the initializaing, and request to create 
its shadow on it. Therefore even the device invisible from the VPN can be operated via the proxy server.

## Thing Description


