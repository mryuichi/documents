# PARTICIPANT PlugFest Result for Lyon 2018

This document summerizes the results of the Lyon PlugFest held Oct 20 and 21.

## 3 Checking Points 

Test results can have one of 4 states:

* OK: Test passed
* NO: Test failed
   * Use "Issue: ..." to note down the reason
   * Comment if there is a known fix
* OT: Out-of-time to complete test
* NA: Test not applicable, e.g., because feature is not implemented
   * Comment if feature is planned to be implemented in the future

### 3.1 Testing Individually
#### 3.1.1 Validate Simplified TDs

* OK
   * Comment: checked Fujitsu TDs using TD Playground.

#### 3.1.2 Register with Thing Directory

* OK/OT
   * Comment: provided Thing Directory at local network
    and Internet. We tried to synchronize TDs of device 
    to be connected to Fujitsu Proxy to ThingWeb directory, 
    but could not connect because ThingWeb directory had stopped.
    (We have checked the synchronization between Fujitsu proxy
    and ThingWeb directory using local ThingWeb directory.)

#### 3.1.3 Connect with Remote/Local Proxy

##### IMPLEMENTATION at URI

* OK
   * Comment: Fujitsu provided Remote/Local Proxy. 

#### 3.1.4 Connect with node-wot

* OK
   * Comment: Fujitsu Remote Proxy could connect with Siemens node-wot, and could control FestLive via Fujitsu Remote Proxy.

#### 3.1.5 Scripting API

* NA

### 3.2 Testing in Client Role
#### 3.2.1 Metadata Handling

* NA

#### 3.2.2 Read Property

##### HTTP

###### 
* OK
   * SiemensIoTDemo
   * SmartThings Lamp and Illuminance Sensor
   * Intel LED Light and Illuminance Sensor (https)
   * Panasonic Device Sim. and Home Devices (https)
   * Fujitsu airPressure sensor
   
##### CoAP

* NA

##### MQTT

* NA

##### Other

###### ECHONET Lite
* OK
   * Fujitsu Illuminance Sensor and LED Light

###### EtherCAT
* OK
   * Fujitsu Rotary Light

#### 3.2.3 Write Property

##### HTTP

###### 
* OK
   * SmartThings Lamp
   * Intel LED Light (https)
   * Panasonic Device Sim. and Home Devices (https)
   
##### CoAP

* NA

##### MQTT

* NA

##### Other

###### ECHONET Lite
* OK
   * Fujitsu LED Light

###### EtherCAT
* OK
   * Fujitsu Rotary Light

#### 3.2.4 Observe Property

##### HTTP+Longpoll

* NA
   * Comment: we checked in online plugfest

##### HTTP+Webhooks

* NA

##### CoAP

* NA

##### WebSockets

* NA

##### MQTT

* NA

##### Other

* NA

#### 3.2.5 Invoke Action

##### HTTP

* NA

##### CoAP

* NA

##### MQTT

* NA

##### Other

* NA

#### 3.2.6 Subscribe Event

##### HTTP+Longpoll

* NA

##### HTTP+Webhooks

* NA

##### CoAP

* NA

##### WebSockets

* NA

##### MQTT

* NA

##### Other

* NA

#### 3.2.7 Security

##### BASIC

###### Intel
* OK
   * Comment: we can control intel devices using basic schema via fujitsu proxy.
   
###### other nosec devices
* OK
   * If a device does not have authentication capability, remote proxy provides basic authentication to the application and rewrites the security metadata in TD for adding a term "basic".

##### BEARER

###### Panasonic
* OK
   * Comment: we can control panasonic devices using basic schema via fujitsu proxy.


#### 3.2.8 Semantic integration

##### PARTNER
* OK/NO/OT/NA
   * Issue: 
   * Comment: 

#### 3.2.9 Accessibility

* NA

### 3.3 Testing in Server Role
#### 3.3.1 Metadata

* NA

#### 3.3.2 Read Property

##### HTTP

###### HITACHI
* OK
   * Comment: HITACHI can read fujitsu devices value.

##### CoAP

* NA

##### MQTT

* NA

##### Other

* NA

#### 3.3.3 Write Property

##### HTTP

###### HITACHI, Panasonic, Oracle
* OK
   * Issue: 
   * Comment: they can control fujitsu devices via proxy

##### CoAP

* NA

##### MQTT

* NA

##### Other

* NA

#### 3.3.4 Observe Property

##### HTTP+Longpoll

* NA

##### HTTP+Webhooks

* NA

##### CoAP

* NA

##### WebSockets

* NA

##### MQTT

* NA

##### Other

* NA

#### 3.3.5 Invoke Action

##### HTTP

* NA

##### CoAP

* NA

##### MQTT

* NA

##### Other

* NA

#### 3.3.6 Subscribe Event

* NA

##### HTTP+Webhooks

* NA

##### CoAP

* NA

##### WebSockets

* NA

##### MQTT

* NA

##### Other

* NA

#### 3.3.7 Security

##### BASIC
   
###### nosec devices
* OK
   * If a device does not have authentication capability, remote proxy provides basic authentication to the application and rewrites the security metadata in TD for adding a term "basic".

#### 3.3.8 Semantic integration

* NA

### 3.4 Other issues

#### 3.4.1 Producing Running Actions and Event Instances

* NA

#### 3.4.2 Consuming Running Actions and Event Instances

* NA

#### 3.4.3 New Security Patterns

* NA

#### 3.4.4 Miscellaneous

* NA

## 4 Use cases

### USE CASE

* OK/NO/OT/NA
   * Issue: 
   * Comment: 
