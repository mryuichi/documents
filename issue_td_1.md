Necessary restriction for the hierarchical defined properties

Thing Description has a great possibility that many things could be described.  However, it could be sometimes difficult to interpret any TDs 
if there is not any restriction on the way to describe TD.  Some restrictions on how to describe TD should be necessary 
because we must have embedded the TD interpreter to the proxy in advance.

This proposal is based on the experience of the past two plugfests.  
Fujitsu provided [the proxy service](https://github.com/mryuichi/documents/blob/master/Plugfest_Outcome_Proxyservice_Fujitsu20201026.pdf) 
that can read TDs members provided first 
and generate shadow devices associated with them automatically. The applications handle shadows on the proxy instead of the physical devices 
since the proxy relays messages between physical and shadow devices.

In the plugfest in June, the proxy could interpret all TDs of accessible devices and enable the application to access them via the proxy. 
However, some TDs could NOT be done in September.  The reason why it doesn't work is the proxy cannot interpret correctly the hierarchically 
defined properties in your TDs.  Until the previous plugfest, all TDs were described with one layer properties, so the proxy succeeded to read 
them and generate shadows from TDs.  However, TUM TDs' properties on this plugfest are defined in three layers 
like "lightinformation", "state" and "on" for [the Hue color lamp](https://github.com/w3c/wot-testing/blob/master/events/2020.09.Online/TDs/TUM/HueColorLight1.td.jsonld), for example.

I don't mean this TD is wrong. I believe these layered property descriptions are necessary, as some standards use such as Broadband forum TR-069, 
eclass, and so on.
