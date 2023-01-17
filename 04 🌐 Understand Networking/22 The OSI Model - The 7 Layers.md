> [!todo]
>  - [ ] 📺 [The OSI Model: A Practical Perspective - Layers 1 / 2 / 3](https://www.youtube.com/watch?v=LkolbURrtTs&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=3)
> - [ ] 📺 [The OSI Model: A Practical Perspective - Layers 4 / 5+](https://www.youtube.com/watch?v=0aGqGKrRE0g&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=4) 
> - [ ] 📺 我在 youtube 上发现的一个 OSI Model 视频 https://www.youtube.com/watch?v=0y6FtKsg6J4
> 

networking has set of rules

OSI Model(Open Systems Interconnection Model)
- is a framwork
- serven different abstraction layers
	- Physical ➡️ Data Link ➡️ Network ➡️ Transport ➡️ Session  ➡️ Presentation  ➡️ Application

## Layer 1 - 7
### Layer 1 - Physical
cables: ethernet | fibre | wi-fi | hubs
transporing bits: 
- data exists in the form of bits(1's & 0's)
- something needs to transport those bits between hosts

### Layer 2 - Data Link
hop to hop delivery
interacts with the cable (⬆️[[#Physical]]): 
- network interface cards(aka nic)
- wi-fi acces cards
- switches
addressing scheme - mac address
- 48 bits, represented as 12 hes digits
- every nic(network interface card) has a unique mac address

### Layer 3 - Network
end to end delivery
addressing scheme - IP addresses
- 32 bits, represented as 4 octets, each 0-255
technology: Routers | hosts | anything with an ip

> [!note] 
> both Layer 2 and Layer 3 need addressing schemes
> Layer 2 - MAC Addresses = Hop to Hop Deliver 🤔 
> Layer 3 - IP Addresses = End to End Deliver 🤔 

[[23 Network Protocols]] - ARP(Address Resolution Protocol) links [[#Layer 2 - Data Link]] and [[#Layer 3 - Network]] addresses

### Layer 4 - Transport
service to service delivery
distinguish data streams
addressing scheme - ports
- 0-65535 - TCP (reliability)
- 0-65535 - UDP (efficiency)
HTTPS: TCP/443
HTTP: TCP/80
IRC: UDP/6667

> [!note] 
> Layer 2 and Layer 3 had addressing schemes **Layer 4 have ports**

### Layer 5, 6, 7 - Session, Presentation, Application
[TCP IP Model](https://www.geeksforgeeks.org/tcp-ip-model/) 值得一看

 hosts 之间 communicating each other 是如何发生的？
 1. host has an applicaition that's going to generate data ➡️ 这个 data 要拿来发送到其他 host 的
 2. data ➡️ [[#Layer 4 - Transport]] add a new header to data ➡️ port (using TCP | UDP)
	 - this new header includes a source port and destination port
	 - this new header + data = segment
 4. segment passed down the OSI stack to [[#Layer 3 - Network]] ➡️ add a new header to this data 
	 - this new header includes a source IP and a destination IP
	 - this new header + data = packet
 5. packet passed down to [[#Layer 2 - Data Link]] ➡️ add a new heade
	 - this new header includes a source and destination MAC address
	 - this new header + data = frame

> [!note] ⬆️每一层都有一个船新的 header

![[Day22_Networking6.png]]
![[Day22_Networking7.png]]![[Day22_Networking8.png]]