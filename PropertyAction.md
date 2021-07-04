>we should check with ECHONET how Actions are used (see slide 16). @mryuichi will check with the ECHONET representatives

In the presentation (see slide 25 [here](https://github.com/w3c/wot/blob/main/PRESENTATIONS/2021-03-online-f2f/2021-03-15-ECHONET-Lite-WebAPI-ECHONET-Consortium.pdf)) of ECHONET lite on the Open day of vf2f, we found that ECHONET Lite device is basically controlled by setting its property in Web API, but there are exceptions.
(1)	Set only property in ECONET Lite is mapped to action in Web API.
(2)	Logical objects such as “bulk” and *group” can be controlled by invoking the action.

Case (1) is defined as only 4 cases in Web API (see [document](https://echonet.jp/wp/wp-content/uploads/pdf/General/Download/web_API/ECHONET_Lite_Web_API_Dev_Specs_v1.3.0.pdf)) at the moment. Reset the cumulative power generation value of Fuel cell, etc.
Case (2) is that multiple operations are defined as one object and it can be executed in one operation with invoking the action. This is a feature that helps application developers.

>@mryuichi will provide a proposal for describing the usage of properties and actions

I found an amazing slide in OCF presentation. (See slide 5 in [here](https://openconnectivity.org/specs/OCF_2.0.2_Specification_Overview.pdf))

This slide shows two approaches to device interface representation. One is to define by device resources and their properties. This definition is equivalent to Property in WoT. The other is to define by device functions and operations. This is equivalent to Action in WoT.
The slide also provides an example of a presentation. In this example, the light bulb is represented in two ways, and the same content can be represented by ether Property or Action.

When describing a device as a property, for example, turning on the switch of the bulb, only the property of the switch is changed after this operation. On the other hand, when describing a device operation with Action, different properties can be assigned to the input and the output of the Action. Therefore, only when the input and the output are the same property, it can be described by both Property and Action.

A quick look at the specifications shows that OCF, KNX, BACnet, and ECHONET are defined based on the property so that these devices are easy to map to both Properties and Actions of WoT.

I would like to write a formal description of the usage of property and action.

>we should also decide if we clarify this in the Architecture document

The definitions of Action and Property in the architecture document are as follows:

>Action
>An Interaction Affordance that allows to invoke a function of the Thing, which manipulates state (e.g., toggling a lamp on or off) or triggers a process on the Thing (e.g., dim a lamp over time).
>Property
>An Interaction Affordance that exposes state of the Thing. This state can then be retrieved (read) and optionally updated (write). Things can also choose to make Properties observable by pushing the new state after a change.

These two definitions say that when you control a device, you’d rather use Action. If we can use both Action and Property, the word “optionally” in the property definition above should be deleted.
