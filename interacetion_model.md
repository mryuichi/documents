@egekorkan, thank you for your comment. I think your comment is appropriate. Sorry for the late reply.

It's great to be able to represent product-specifc specifications with TD. But at same time, I'm worried it might build silos over the WoT.
WoT's goal was to ensure interoperability between various standards and to eliminate the silos. In order to achive this, we need some guidelines on createing a TD. This should be discussed in the Profile TF.
On the other hand, I think we should define TDs so that it can be represented simply without converting the existing stadandards as much as possible. After a quick look at some of the standards, the propery, the event, and the action defined on TD correspond to them as follows:

|standards|property|event|action|
|---|---|---|---|
|WoT|property|event|action|
|OPC UA|attribute|event|method|
|Azure DTDL|property|event|command|
|OCF|property|event||
|KNX|property|event||
|ECHONET Lite|property|event||
|BACnet|property|event||
|NGSI|property|event||
|Mozilla WebThing|property|event|action|

(If you are an expert for these standards, please check if these are correct. The blank shows no correspoinding item.)

In these standards, the devices can be operated by changing the value of the property (using WriteProperty) instead of invoking the action. Therefore, I think the description of the WoT documents should be modified so that the device can be operated by writing the property in TD as well.

