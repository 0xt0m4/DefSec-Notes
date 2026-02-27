
# ISO's OSI Model

The Open Systems Interconnection breaks down how network devices operating with data, invented from the Internal Organization for Standardization.
Here is a breakdown:


1. **Physical**:
	data cables, antennas
2. **Data**:
	Sending data in a network segment (on a switch), MAC address
3. **Network**
	Sending data between different networks (IP address), routing
4. **Transport**:
	Typically protocols (TCP/UDP)
5. **Session**
	Establishing and managing the communication (the current session) (NFS/RPC)
6. **Presentation**
	Ensures the data delivered in a form the application layer can understand (JPEG, MOV)
7. **Application**
	HTTP, SMTP, DNS


And remember:

==Please Do Not Throw Sausage Pizza Away!==



# TCP/IP Model


7: Application Layer
	In the TCP/IP model, the application layer is basically contains the presentation and session layers. The TCP/IP model's application layer is from **the 5th 6th and 7th all together**!

4: Transport Layer 
	The transport layer `._.`

3: Internet Layer
	The OSI model's network layer is called **internet layer** in the TCP/IP model.

2: Link Layer
	This is layer 2. `._.`


# IP Addresses & Subnets

In order for a host on the network, to communicate with each other, needs an IP address. This done via IPv4.

`192.168.1.0` is reserved for network address, and
`192.168.1.255` is reserved for the broadcast.

Therefore this range can hold not 256, but 254 hosts (1-254)

## Private and Public IP Addresses

RFC 1918 defines the following three ranges of private IP addresses:

- `10.0.0.0` - `10.255.255.255` (`10/8`)
- `172.16.0.0` - `172.31.255.255` (`172.16/12`)
- `192.168.0.0` - `192.168.255.255` (`192.168/16`)

In order for an IP address to be public, the router must have a public IP, and must support NAT.

## Routing

Like the local post office:
You hand them the mail parcel, and they would know how to deliver it


# TCP & UDP

![[Pasted image 20260129232042.png]]


- UDP (User Datagram Protocol):
	A simple protocol operates at layer 4. 
	Famous from it's **speed** and **unreliability**

- TCP (Transmission Control Protocol):
	Known for it's **reliability** over speed
	Before any data can be sent, it requires and establishment:
	A **three-way handshake**:
	1. SYN(Synchronise) Packet:
		The client initiates the connection by sending a SYN packet
	2. SYN-ACK Packet:
		The server responds with a SYN-ACK
	3. ACK(Acknowledgement) Packet:
		The 3-way handshake completed as the client sends an ACK packet
	![[5f04259cf9bf5b57aed2c476-1719849036216.svg]]


# Encapsulation

It's a process of every layer adding a header (and sometimes a trailer) to the recieved unit of data, sending the "encapsulated" unit to the layer. 
==wrapping data in layers, like a package inside a package inside a package.==

 **Why this is important**

Encapsulation lets:

- Apps not worry about routing
    
- Routers not worry about apps
    
- Wi-Fi not worry about TCP

![[5f04259cf9bf5b57aed2c476-1719849061418.svg]]
- Segment (TCP) / Datagram (UDP) → Transport layer  
    Data + port numbers (which app is talking)
    
- Packet (IP)** → Network layer  
	Segment/datagram + IP addresses (which computers)
    
- Frame (Ethernet/WiFi)** → Data link layer  
    Packet + MAC addresses (how it moves on the local network)


# DHCP

The _Dynamic Host Configuration Protocol_ is an application level protocol, which is essential for automatizing devices network setup. Especially for phones, and also so IPv4 addresses won't be duplicated, it is crusual for a normal network!


In order for network access, the following are essentials:
- **IP address** along with **subnet mask**
- **Gateway** (or router)
- **DNS** server


The process looks like the following:

1. **DHCP Discover**: The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.
2. **DHCP Offer**: The server responds with a DHCPOFFER message with an IP address available for the client to accept.
3. **DHCP Request**: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.
4. **DHCP Acknowledge**: The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.

![A laptop sends a DHCP Discover, the server responds with a DHCP Offer, the laptop responds with a DHCP Request, and finally, the server responds with a DHCP Acknowledge.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/5f04259cf9bf5b57aed2c476-1719849148646.svg)
 