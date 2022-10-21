
> [!note]
> 📽️ [Subnet Mask - Explained](https://www.youtube.com/watch?v=s_Ntt6eTn94&list=WL&index=1) 
> 个人觉得这个视频比看文字好多了，多看几遍反而更能理解

----

video form ⬇️ 
📽️ [Network Protocols - ARP, FTP, SMTP, HTTP, SSL, TLS, HTTPS, DNS, DHCP](https://www.youtube.com/watch?v=E5bSumTAHZE&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=12)
Internet Standard ➡️  [RFC 826](https://datatracker.ietf.org/doc/html/rfc826)

Protocols
- ARP - Address Resolution Protocol
- FTP - File Transfer Protocol
- SMTP - Simple Mail Transfer Protocol
- HTTP - Hyper Text Transfer Protocol
- SSL - Secure Sockets Layer | TLS - Transport Layer Security
- HTTPS - HTTP secured with SSL/TLS
- DNS - Domain Name System
- DHCP - Dynamic Host Configuration Protocol

each host requires these 4 things
- IP Address
	- e.g. 192.168.169.2
- Subnet Mask
	- you can think of this as postcode or zip code.
	- size of hosts network
	- e.g. 255.255.255.0
- Default Gateway 
	- You could think of this as the single road that allows us out of our street
	- router's IP address, providing us with that Layer 3 connectivity
	- e.g 192.168.169.1
- DNS
	- e.g. 192.168.169.254 | 8.8.8.8

> if you have 1000 or 10,000 hosts then that is going to take you a very long time to determine each one of these individually. This is where DHCP comes in and allows you to determine a scope for your network and then this protocol will distribute to all available hosts in your network.

⬆️ 翻译出来我都看不懂
⬇️ 那我们就举个例子吧

>  When you connected to the coffee shop WiFi your machine would have picked up a DHCP address either from a dedicated DHCP server or most likely from the router also handling DHCP.

### Subnetting

> [!note]
> 这边的解释还挺难理解的，感觉看这个 [subnet mask](https://youtu.be/s_Ntt6eTn94?t=610)就好了
> the way to break this network down into smaller networks is by subnetting
> 

优点
- run more efficiently
- nable IP address reallocation and relieves network congestion, streamlining, network communication and efficiency
- improve network security

 