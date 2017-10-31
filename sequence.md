# Sequence Diagrams

## 1. Preparation
### 1.1 Use Case
One or more base uri are assigned to the servients to enable to be access from remote and local servients.

![images](/images/UseCase.png)

### 1.2 Things directories on proxy servients
The figure shows below is a directory structure for management of things in a servient. This example is the thing directory for the remote proxy servient “remoteProxy”, Base url for the remote proxy servient. 

![images](/images/ThingDirStructure.png)

## 2. Sequence diagrams
### 2.1 Register
A device servient is registered to the local proxy servient and remote proxy servient. The proxy servient returned the TD with public uri. The proxy servients have TD repositories to store TDs registered from the other servients.

![images](/images/seq_register.png)

(1) HTTP POST http://lps.example.com/Things/register<BR>
Body: TD<BR>
(2) 201 Created<BR>

(3) (1) HTTP POST http://lps.example.com/Things/register<BR>
Body: TD<BR>

(4) 201 Created<BR>

## 2.2 Lookup
An application servient can lookup TDs registered the remote proxy servient with its URI. If the URI indicates the servient, it returns the list of the devices connected. If the URI specifies the devices registered on the proxy servient, it returns TD of it.

![images](/images/seq_lookup.png)

(11) HTTP GET http://rps.example.com/Things/<BR>
Body: none<BR>

(12) 200 OK<BR>
Body: list of registered things [FujitsuAirConditioner, PanasonicAirConditioner, …]<BR>

(13) HTTP GET http://rps.example.com/Things/deviceName<BR>
Body: none<BR>

(14) 200 OK<BR>
Body: TD

## 2.3 Get property
The application servient sends a request to get the value of the property of the device servient to the remote proxy servient. The remote and local proxy servient relay to this request to the device servient.

![images](/images/seq_getproperty.png)

The application gets a value of a certain property of the device servient. For this purpose, it gets the URI for the property from TD of the device servient.
(21) HTTP GET http://rps.example.com/lps1/Things/deviceName/Property/temperature<BR>
Body: none<BR>

The remote proxy gets the URI for the property from TD of the device servient registered in the repository. "glps.example.com" is global address which can be accessed from remote proxy.
(22) HTTP GET http://glps.example.com/Things/deviceName/Property/temperature<BR>
Body: none<BR>

The local proxy gets the URI for the property from TD of the device servient registered in the repository.
(23) HTTP GET http://192.169.1.2/Things/deviceName/Property/temperature<BR>
Body: none<BR>

(24) 200 OK<BR>
Body: 25(value)<BR>

(25) 200 OK<BR>
Body: 25(value)<BR>

(26) 200 OK<BR>
Body: 25(value)<BR>

## 2.4 Set property
The application servient sends a request to set the value to the property of the device servient to the remote proxy servient. The remote and local proxy servient relay to this request to the device servient.

![images](/images/seq_setproperty.png)

The application puts a value of a certain property of the device servient. For this purpose, it gets the URI for the property from TD of the device servient.
(31) HTTP PUT http://rps.example.com/lps1/Things/deviceName/Property/status<BR>
Body: ON<BR>

The remote proxy puts the URI for the property from TD of the device servient registered in the repository.
"glps.example.com" is global address which can be accessed from remote proxy.
(32) HTTP PUT http://glps.example.com/Things/deviceName/Property/status<BR>
Body: ON<BR>










