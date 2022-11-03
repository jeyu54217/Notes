**CONTENTS**

- [Network Scope](#network-scope)
  - [PAN (Personal Area Network)](#pan-personal-area-network)
  - [LAN (Local Area Network)](#lan-local-area-network)
  - [MAN (Metropolitan Area Network)](#man-metropolitan-area-network)
  - [WAN (Wide Area Network)](#wan-wide-area-network)
- [Topology](#topology)
- [Physical layer](#physical-layer)
  - [Protocols](#protocols)
    - [Token ring](#token-ring)
    - [CSMA/CD](#csmacd)
    - [CSMA/CA](#csmaca)
  - [Connection ways](#connection-ways)
    - [Compatible Networks](#compatible-networks)
      - [Repeater](#repeater)
      - [Bridge](#bridge)
      - [Switch](#switch)
    - [Incompatible Networks](#incompatible-networks)
      - [Router](#router)
- [Network Application Architectures](#network-application-architectures)
  - [Client-Server](#client-server)
    - [Server](#server)
    - [Client](#client)
  - [P2P](#p2p)
  - [Hybrid](#hybrid)
- [Processes Communicating](#processes-communicating)
  - [Process](#process)
  - [](#)
  - [Socket](#socket)
  - [API](#api)
- [REFERECES](#refereces)

# Network Scope
## PAN (Personal Area Network)
  -  A network formed around a person
  -  e.g. cordless mice, keyboards, Bluetooth systems.
- Pros.
  - secure & safe
  - It offers only short-range solution up to 10 meters
- Cons.
  - Should be in the same radio bands.
  - Distance limits.
## LAN (Local Area Network)
  -  a group of computer which are connected in a limited area such as school, laboratory, office building or a printer in someone’s home
  -  For sharing resources like files, printers, games, and other application. 
  -  Consists of less than **5000** interconnected devices across several buildings.
- Pros.
  - File sharing
      - hard-disks, DVD-ROM, and printers can share local area networks. This significantly reduces the cost of hardware purchases.
      - You can use the same software over the network instead of purchasing the licensed software for each client in the network.
      - Data of all network users can be stored on a single hard disk of the server computer.
      - You can easily transfer data and messages over networked computers.
      - It will be easy to manage data at only one place, which makes data more secure.
- Cons.
  - Initial cost : the initial cost of installing Local Area Networks is quite high.
  - Privacy : The LAN admin can check personal data files of every LAN user, so it does not offer good privacy.
  - Unauthorized users can access critical data of an organization in case LAN admin is not able to secure centralized data repository.
  -  requires a constant LAN administration as there are issues related to software setup and hardware failures

## MAN (Metropolitan Area Network)
  -  a computer network across an entire city, college campus, or a small region. 
  -  This type of network is large than a LAN, which is mostly limited to a single building or site. 
  -  It mostly covers towns and cities in a maximum 50 km range
  -  Mostly used medium is optical fibers, cables.
  - ![image](https://www.guru99.com/images/1/090719_0501_TypesofComp4.png)
- Pros.
  - It offers fast communication using high-speed carriers, like fiber optic cables.
  - It provides excellent support for an extensive size network and greater access to WANs.
- Cons.
  - You need more cable to establish MAN connection from one place to another.
  - In MAN network it is tough to make the system secure from hackers
## WAN (Wide Area Network)
  - spread across a large geographical area such as small towns, cities 
  - Could be a connection of a LAN which connects with other LAN’s using telephone lines and radio waves
  - It is mostly limited to an enterprise or an organization.
  - The software files will be shared among all the users; therefore, all can access to the latest files.
  - Any organization can form its global integrated network using WAN.
- Pros.
  - business offices situated at longer distances can easily communicate.
  - Contains devices like mobile phones, laptop, tablet, computers, gaming consoles
  - WLAN connections work using radio transmitters and receivers built into client devices.
- Cons.
  - The initial setup cost of investment is very high.
  - It is difficult to maintain the WAN network. You need skilled technicians and network administrators.
  - There are more errors and issues because of the wide coverage and the use of different technologies.
  - It requires more time to resolve issues because of the involvement of multiple wired and wireless technologies.
  - Offers lower security compared to other types of network in computer.

# Topology
  - ![image](https://assets-global.website-files.com/620d42e86cb8ec4d0839e59d/6230eed9d9792f3709c5ffd6_5f1086baa37c842a30184650_network-topology-types-diagram.png)
  (source: [heavy.ai-network-topology](https://www.heavy.ai/technical-glossary/network-topology))
  - see also : https://en.wikipedia.org/wiki/Network_topology
  1. Ring
  2. Star  
  3. Bus 
  4. Hub 
# Physical layer 
## Protocols
### Token ring
  - Popular in ring topology.
  - Token and messages are passed in one direction.
  - Only the machine that gets the token can transmit its own message.
### CSMA/CD 
  - Wired, carrier sense, multiple access with collision detection
	- Popular in bus topology (wired Ethernet).
	- Broadcasting.
	- When collision, both machines wait for a brief random time before trying again.
### CSMA/CA 
  - Wireless, carrier sense, multiple access with collision avoidance
	- Popular in wireless Ethernet.
	- Broadcasting.
  - Detect if a channel is idle, if so, wait for a brief random time and then detect again. If the channel is still idle, start to send.
## Connection ways
### Compatible Networks
   - Use the same Protocol
#### Repeater
  - Simply passing through messages.（boardcasting to all）
  - Connecting 2 compatible networks.
#### Bridge 
  - Can reduce collision better than repeater
  - Connecting two compatible networks more efficiently.
#### Switch  
  - A bridge with multiple connections (multi bus connection)
  - Connecting several compatible networks mor e efficiently.
### Incompatible Networks 
  - Use different potocols
#### Router
  - Building a network of networks, known as an internet.
	- 會拆開封包重包裝分送
	- Most come with firewall management.
# Network Application Architectures
- an application’s architecture is distinctly differ- ent from the network architecture (e.g., the five-layer Internet architecture)
- The application architecture, on the other hand, is designed by the application developer and dictates how the application is structured over the various end systems.
## Client-Server
 ![image](https://miro.medium.com/max/595/0*8PDbGCkKG0j1Cp4F.png)
- Client-Server Architecture | Source : https://cio-wiki.org/wiki/Client_Server_Architecture
- e.g. Web, FTP, Telnet, e-mail
- Overwhelmed : single-server host is incapable of keeping up with all the requests from clients
- Data center : virtual server which is housing a large number of server hosts
### Server
- an always-on host
- has a fixed, well-known address -  IP address
- services requests from many other hosts -> clients
### Client
- clients do not directly communicate with each other
## P2P
 ![image](https://www.researchgate.net/profile/Erkki-Harjula/publication/224305552/figure/fig2/AS:667774380679177@1536221227291/Peer-to-peer-data-management-architecture.png)
  - P2P Architecture | Source : https://www.researchgate.net/figure/Peer-to-peer-data-management-architecture_fig2_224305552
  - peer : direct communication between pairs of intermittently connected hosts, 
  - Self-scalability : each peer also adds service capacity to the system by distributing files to other peers
  - face challenges of security, performance, and reliability due to their highly decentralized structure.
## Hybrid
- i.e. Instant messaging applications
    - server : used to track the IP addresses of users
    - P2P : user-to-user messages
    - 
# Processes Communicating
## Process
- a program that is running within an end system
## 
## Socket
- The Interface Between the Process and the Computer Network
- The interface between the application layer and the transport layer within a host
## API 
- Application Programming Interface


The application developer has con- trol of everything on the application-layer side of the socket but has little control of the transport-layer side of the socket. The only control that the application developer has on the transport-layer side is (1) the choice of transport protocol and (2) perhaps the ability to fix a few transport-layer parameters such as maximum buffer and maxi- mum segment sizes (to be covered in Chapter 3). Once the application developer chooses a transport protocol (if a choice is available), the application is built using the transport-layer services provided by that protocol.
# REFERECES
- [Introduction to Computer Science](http://ocw.aca.ntu.edu.tw/ntu-ocw/ocw/cou/101S210)
- [Types of Computer Network: What is LAN, MAN and WAN](https://www.guru99.com/types-of-computer-network.html)
