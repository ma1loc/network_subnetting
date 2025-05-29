
<h1 align="center">Network Basics and Subnetting</h1>

<p align="center">
  <img src="https://github.com/user-attachments/assets/a42ce875-b73e-4b8a-b6ad-a9fbc1e99ee5" width="600"/>
</p>

First of all, all the information here is taken from the CISCO CCNA knowledge, to help people push the NetPractice project of 1337/42 school, and the purpose is just to simplify the project for others and refresh the project concepts for better understanding.

## What you will learn here:
- What is an IP?
- What is a MAC?
- What is a router?
- What is a switch?
- What is subnetting?
- What are the types of networks?
- what is DHCP?
- And a lot of things to check out for yourself.

---

## What is an IP address?

**IP** stands for **Internet Protocol**, which means it is an internet address. Without it, we cannot access the internet.

We have two different types of IPs: **IPv4** and **IPv6**.  
Here we will talk about **IPv4**, as it is most used nowadays.

IPv4 also has two types: **private IP** and **public IP** addresses. Let's talk briefly about the purpose of each one:

- The **private IP address** is a unique address in the LAN (Local Area Network), and with it, we can access all the devices in the LAN.  
- As I said, it’s just for the LAN — meaning we cannot use it to access the internet.

- The **public IP address** is unique in the public network, which means no one has your public IP address in the public network. This IP is provided by the ISP(Internet Service Provider)
Like here in Morocco, we have "Maroc Telecom" as an ISP, for example, that provides you with an IP address, but the question is, what makes it unique? Is it not duplicated?
the answer of the qusiton is the IANA(Internet Assigned Numbers Authority), manages three critical internet components: IP addressing, DNS root zone management, and protocol parameters, serving as the global coordinator for these essential resources. While operating under ICANN's structure, IANA maintains operational independence in managing internet's core numbering systems.
- We can say that the IANA gives a pool of IPs to the ISPs, who then divide them and assign them to users of the internet. We pay for the IP address that gives us the ability to access the internet.

**Bonus:** IP addresses have 5 classes you need to know.  
You have a range of classes you can use based on the number of LAN devices. If you have more than 256 devices, you will not use **Class C**.

---

## The 5 Classes:

- **Class A** → `10.0.0.0/8`
- **Class B** → `172.0.0.0/16`
- **Class C** → `192.168.0.0/24` → This is the most famous one used in a home LAN.
- **Class D** → NOT USED (reserved)
- **Class E** → NOT USED (reserved)

---

> Picture from -> [Here](https://www.tecmint.com/network-ip-addressing-range/)  
![Classes-of-IP-Addresses](https://github.com/user-attachments/assets/b36c02bc-eb69-496b-8957-0dc743153f26)


- **Class A** gives us a range of `2^24` (24 bits free), which is 16,777,216 addresses — a huge number for a HOME LAN. That’s why it’s not popular there.
- **Class B** gives `2^16 = 65,536` IPs — good for a medium-sized LAN.
- **Class C** gives `2^8 = 256` devices in the LAN network, which is perfect for a small home network.

---

## Let's talk about the **gateway** and the **broadcast** of an IP address (IPv4):

You might ask: Why not 255 and 256?  
Here’s the idea: the first address (ending in `.0`) is the **network address**, and the last one (ending in `.255`) is the **broadcast address**.  
These two are **not used for devices**, which leaves you with 254 usable addresses in a `/24` range.

---

### What is the broadcast?

Imagine we have a protocol like **ARP** (you can learn about this protocol if you're interested).  
Every time ARP wants to get the MAC address of another device, it only knows that device's IP address.  

Since it doesn’t know the exact path or location of that device, it uses the **broadcast address** (the last IP in the subnet) to send the request to **everyone** in the network, asking who has that IP address.

You cannot assign a broadcast IP to a device — it’s only used for communication with **all** devices.

---

## What is the network address and the gateway?

Let’s talk first about the **network address**.

Imagine we have a lot of networks. Before specifying the IP address of a destination device, we must know the network address of that destination, because within a larger network, there can be many smaller subnetworks.

> (To better understand this, look at the picture below.)  

<img width="1729" alt="shapes at 25-05-27 10 42 26" src="https://github.com/user-attachments/assets/9ed73955-efe0-4fc2-a75e-d5026a613f8f" />  
  
  
> Picture from → [Here](https://mockflow.com/flowchart-examples/cisco-network-diagram-example-network-address-translation)

- **The network address** – to know which network the destination is part of.  
- **The host (device) address** – to know which device inside that network you want to reach.  

In IPv4, this is handled by dividing the IP address into:  
- **Network part** (based on the subnet mask, like `/24`)  
- **Host part** (specific to the device)  

Let’s talk first about the **gateway address**.
As your device has an IP address, the router(we will talk about it later on) has an IP, and if we talking about the IP address, we will use the public one to get the internet


Example:
If the IP is 192.168.1.42/24:  
    Network address = 192.168.1.0  
    Host address = 42 (the unique ID of the device in that network)  
In summary, the Gateway IP address should not be assigned to any device within the Local Area Network (LAN), because it is reserved for the router or gateway itself. The gateway serves as the only path through which devices in the LAN can access external networks, such as the Internet.  

**NOTE:** In the LAN, everyone has a unique private IP address. But for public IP, we usually have just one in the LAN.  
But how do all the users in the LAN use just one **public IP address**?

If you think about it, we are 8 billion people in the world, and the number of IPv4 addresses possible is only around 4 billion.  
This is the reason why we use **private IPs in the LAN** with **one public IP**, which increases IPv4 efficiency.  

If all the LAN users access the internet, will it work fine? Why?  
Can all the users use the same public IP address at the same time?

The answer is **YES** — there's a protocol running in the **Network layer** called **NAT** (Network Address Translation) that helps multiple devices on a private network (LAN) share a single public IP address when connecting to the internet.

> Picture from -> [Here](https://geekflare.com/cybersecurity/network-address-translation/)

![11w-1 (1)](https://github.com/user-attachments/assets/dd3725df-6473-4c56-932e-de00d796dc2a)  
This process is typically managed by a router or firewall, which translates private IP addresses into public ones and back again (you can read more about this protocol (NAT) [Here](https://www.geeksforgeeks.org/network-address-translation-nat/)).

## What is the router?
**< Router icon >**
<p align="center">
  <img src="https://github.com/user-attachments/assets/b96cb1b5-c93e-4fff-ac09-a9ceedc40c75" width="400"/>
</p>

The router is a physical device that looks like this in the real world:  
<p align="center">
  <img src="https://github.com/user-attachments/assets/f11bdc06-47b4-4bbc-ac15-359047fc383d" width="600"/>
</p>



As the name suggests, a router is for routing — meaning redirecting something to someone else.  
The router, as a physical device, operates at the **Network Layer (Layer 3)** of the OSI model.

Here, we will talk about something this layer adds to the data from the layer above — the **network layer header**.  
The router adds this information in what is called the header, which includes details like the **source IP** and the **destination IP**, and attaches it to the data the network layer receives.

Routers are responsible for forwarding data **between different networks**.  
Unlike switches (which work within a single LAN), routers are the devices that decide the best path for a packet to travel across networks (using routing tables).

They also:
- **Connect LANs to the Internet**
- **Perform NAT (Network Address Translation)** to allow multiple private IPs to share one public IP
- **Drop or forward packets** based on destination IP, routing rules, or policies
- Support **dynamic routing protocols** (like OSPF, RIP, BGP) or **static routes**

### Q&A about the router
-> Q: How does a router find the destination path among so many devices on the internet?

-> A:
Routers use special networking protocols to determine the best and shortest path to the destination. These protocols are designed to handle complex routing decisions efficiently, even with millions of devices on the internet.

There are two main types of routing:

Dynamic Routing – The router uses protocols like

OSPF (Open Shortest Path First)

RIP (Routing Information Protocol)

BGP (Border Gateway Protocol)
These protocols allow routers to automatically exchange information and update their routing tables based on changes in the network.

Static Routing – The paths are manually set by a network administrator. This gives more control but is harder to manage, especially in large networks with many possible paths.

So, routers don’t guess; they follow well-defined rules and protocols to find the most efficient route to the destination.

-> Q: What is the main job of a router in a network?

-> A:
A router’s main job is to connect different networks together and forward data packets between them. It reads the IP address in each packet and decides the best path for the packet to reach its destination.

For example, at home, your router connects your local network (LAN) to the internet (WAN), allowing your devices to communicate with websites, servers, or services around the world.

-> Q: Can a router assign IP addresses?

-> A:
Yes, many routers can assign IP addresses using a service called DHCP (Dynamic Host Configuration Protocol).

When a new device connects to the network, the router automatically gives it an IP address, along with other important settings like the subnet mask, gateway, and DNS server. This makes it easier to manage devices without manually setting IPs for each one.

### What is the DHCP?
DHCP (Dynamic Host Configuration Protocol) is a network protocol that allows devices on a network to automatically receive an IP address and other network settings (like subnet mask, gateway, and DNS).

<p align="center">
  <img src="https://github.com/user-attachments/assets/abe2787a-2fff-45b2-bbff-ca48b579da5f" width="400"/>
</p>

Instead of manually configuring IPs for every device, DHCP saves time and reduces errors by assigning them dynamically.

If you understand how DHCP works, you’ll find tools like NetPractise much easier—because without DHCP, you'd have to configure IP addresses manually for each device on the network.

So in short:

DHCP = automatic IP address assignment

Without DHCP = manual IP configuration for each device

However, not all routers are DHCP servers by default—it depends on the configuration and the type of router.

> In summary: a switch connects devices within a LAN, but a router connects different LANs or connects a LAN to the Internet.

## What is the switch?
**< Switch icon >**
<p align="center">
  <img src="https://github.com/user-attachments/assets/8c3bb1fc-712a-48a9-90b2-49089712d515" width="400"/>
</p>

The switch is a physical device that looks like this in the real world:   
<p align="center">
  <img src="https://github.com/user-attachments/assets/35ec730d-8afc-439a-8cc9-983f8e4004dc" width="600"/>
</p>

A switch is a physical device that operates mainly at Layer 2 (the Data Link Layer) of the OSI model—not the physical layer. It uses MAC addresses to forward data between devices in a Local Area Network (LAN).

Just like IP packets have a source and destination IP address, Ethernet frames have a source and destination MAC address.

Unlike IP addresses, which can change depending on the network, MAC addresses are unique and assigned by the device manufacturer (like Intel, Samsung, etc.). These addresses are used by switches to determine where to forward network traffic.

<p align="center">
  <img src="https://github.com/user-attachments/assets/710eb162-cebb-42cd-9755-801c77508b3a" width="600"/>
</p>

> This is a weird NIC card in the picture looks like  
>  It can be wireless and wired  

Each device uses a Network Interface Card (NIC) to connect to a network—whether it’s a Local Area Network (LAN) or a global network like the internet.

Every NIC has a MAC address, which is a unique physical address assigned by the manufacturer. This address helps identify the device on the network.

While it is possible to change the MAC address temporarily through software (a process called MAC spoofing), the original physical MAC address is hardcoded into the hardware and cannot be fully changed.
If you want to change your MAC address, you can use this script that I built. Check it out [Here](https://github.com/ma1loc/mac_addr_changer)

## The MAC address format looks like this


![pngegg-Photoroom](https://github.com/user-attachments/assets/207cf9e5-ee2c-41c3-80ef-ac8def032e24)


> summary: "A MAC address represents your identity on a network, like a fingerprint for your device on both the internet and local LAN."  

## Type of the networks?

There are three old network infrastructures: bus topology, ring Topology, and we will skip it (not used anymore).  

The most used these days is the **star topology** and an extended-star topology in the LAN:  

<h3 align="center">Star topology</h3>

> Picture from -> [Here](https://blog.boson.com/bid/87993/back-to-the-basics-networks-and-topologies)
<p align="center">
  <img src="https://github.com/user-attachments/assets/926e051f-e4c0-41f6-a5d2-db493d9c8beb" width="600"/>
</p>


A **star topology** is the most common network layout used in **home** and **office** environments.  
It is typically implemented with **unshielded twisted-pair (UTP)** Ethernet cables, but can also use **fiber-optic** or **coaxial** cables.

In this design, **all devices connect to a central device**, such as a **hub** or a **switch**.  
When one device sends data, it first travels to the central device, which then forwards it to the intended recipient.  
Unlike bus or ring topologies, data does **not** need to pass through other nodes.


### Advantages:
- **Better performance** – data avoids unnecessary nodes.
- **Fault-tolerant** – if one device or cable fails, the rest still work.

### Disadvantage:
- **Single point of failure** – if the central hub or switch goes down, the entire network stops working.

<h3 align="center">Extended-Star Topology</h3>

> Picture from -> [Here](https://blog.boson.com/bid/87993/back-to-the-basics-networks-and-topologies)
<p align="center">
  <img src="https://github.com/user-attachments/assets/65c8f919-d5df-4ad7-ae77-d3d248c6137b" width="600"/>
</p>

An extended-star topology builds on the traditional star topology by allowing connections over greater distances. It does this by adding repeaters or additional networking devices between the central switch and the end nodes.

This setup is especially useful in larger physical environments, like big corporate offices, where signal degradation could be an issue over long distances.

While adding extra devices introduces more potential points of failure, the design still makes it relatively easy to identify and isolate problems. If one segment goes down, devices on other segments can still communicate. However, just like in a regular star topology, if the central device fails, the entire network will be affected, and no communication will be possible.

> there's other topology like; mesh, full-mesh, and more you can find it [Here](https://blog.boson.com/bid/87993/back-to-the-basics-networks-and-topologies)

# >>> NOT FINISHED YET
