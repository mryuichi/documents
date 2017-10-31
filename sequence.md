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

*Example: using HTTP*

(1) HTTP POST http://lps.example.com/Things/register<BR>
Body: TD<BR>
(2) 201 Created<BR>

(3) (1) HTTP POST http://lps.example.com/Things/register<BR>
Body: TD<BR>

(4) 201 Created<BR>

## 2.2 Lookup
An application servient can lookup TDs registered the remote proxy servient with its URI. If the URI indicates the servient, it returns the list of the devices connected. If the URI specifies the devices registered on the proxy servient, it returns TD of it.

![images](/images/seq_lookup.png)

*Example: using HTTP*

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

*Example: using HTTP*

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

*Example: using HTTP*

The application puts a value of a certain property of the device servient. For this purpose, it gets the URI for the property from TD of the device servient.

(31) HTTP PUT http://rps.example.com/lps1/Things/deviceName/Property/status<BR>
Body: ON<BR>

The remote proxy puts the URI for the property from TD of the device servient registered in the repository.
"glps.example.com" is global address which can be accessed from remote proxy.

(32) HTTP PUT http://glps.example.com/Things/deviceName/Property/status<BR>
Body: ON<BR>

## 2.5 Subscribe and Event
The application servient sends a request to subscribe the property of the device servient to the remote proxy servient. The device servient keep to send the value of the specified property periodically.

![images](/images/seq_subscribe.png)

*Example: using HTTP*

The application subscribes an event of the device servient to be periodically notified. The application gets URI for this event and send a request to the remote proxy servient.

(41) HTTP POST http://rps.example.com/lps1/Things/deviceName/Event/change<BR>
Body: none<BR>

The remote proxy gets the URI for the event from TD of the device servient registered in the repository.

(42) HTTP POST http://glps.example.com/Things/deviceName/Event/change<BR>
Body: none<BR>

The local proxy gets the URI for this event from TD of the device servient registered in the repository.

(43) HTTP POST http://192.169.1.2/Things/deviceName/Event/change<BR>
Body: none<BR>

The device servient sends a notify to the application via the local and remote proxy servient with Server Sent Events specified by W3C.  The device responses “200 OK” with a header “Context-Type: text/event-stream”.

(44)-(46) 200 OK<BR>
Context-Type:text/event-stream<BR>
Body: none<BR>

If this subscription succeeded, the events keep to be notified to the application via the local and remote proxy servients. This event is sent as chunk data.

(47)-(49) <BR>
Body: data:25(value)<BR>

## 2.6 Unsubscribe
The application servient sends a request to unsubscribe to the remote proxy servient to stop to notify the event from the device servient.

![images](/images/seq_unsubscribe.png)

*Example: using HTTP*

The application unsubscribes the event “change. The application deletes URI for this event and send a request to the remote proxy servient.

(51) HTTP DELETE http://rps.example.com/lps1/Things/deviceName/Event/change<BR>
Body: none<BR>

The remote proxy gets the URI for the event from TD of the device servient unregistered in the repository.

(52) HTTP DELETE http://glps.example.com/Things/deviceName/Event/change<BR>
Body: none<BR>

The local proxy gets the URI for this event from TD of the device servient unregistered in the repository.

(53) HTTP DELETE http://192.169.1.2/Things/deviceName/Event/change<BR>
Body: none<BR>

The device servient stops sending event and returns the response with “200 OK”.

(54)-(56) 200 OK<BR>
Body: none<BR>

### 2.7 Unregister
The device servient unregister from the local proxy servient before shutdown. The local proxy servient unregister this device servient from the remote proxy not to access from the application.

![images](/images/seq_unregister.png)

*Example: using HTTP*

(61) HTTP DELETE http://lps.example.com/Things/deviceName<BR>
Body: none<BR>

(62) 200 OK<BR>
       Body:none<BR>

(63) HTTP POST http://rps.example.com/Things/deviceName<BR>
Body: none<BR>

(64) 200 OK<BR>
Body:none<BR>

