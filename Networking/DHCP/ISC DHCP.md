---
tags:
  - Networking
---
ISC DHCP (Internet Systems Consortium Dynamic Host Configuration Protocol) is an open-source software package that provides a framework for passing configuration information to network devices. It is widely used to automatically assign IP addresses and other network configuration parameters (such as subnet mask, default gateway, and DNS servers) to devices on a network, allowing them to communicate effectively.

Key features of ISC DHCP include:

1. **Dynamic IP Address Allocation**: Automatically assigns IP addresses to devices from a predefined pool of addresses.
2. **Static IP Address Assignment**: Allows for the assignment of fixed IP addresses to specific devices based on their MAC addresses.
3. **Lease Management**: Manages the leasing of IP addresses, including renewal and expiration of leases.
4. **Support for DHCP Options**: Provides additional configuration parameters to clients, such as [[DNS]] servers, NTP servers, and more.
5. **Scalability**: Can be used in small networks as well as large enterprise environments.
6. **Cross-Platform**: Available for various operating systems, including Linux and Unix.

ISC DHCP consists of two main components:

1. **[[DHCP]] Server (dhcpd)**: The server component that assigns IP addresses and configuration parameters to clients.
2. **[[DHCP]] Client (dhclient)**: The client component that requests an IP address and configuration parameters from a DHCP server.

ISC DHCP is highly configurable and can be tailored to meet the specific needs of different network environments. It is widely used in both enterprise and home networks due to its robustness and flexibility.