---
tags:
  - Networking
---
NTP stands for Network Time Protocol. It is a [[Efforts/Ongoing/TheTechMokey/Networking/Networking]] protocol designed to synchronize the clocks of computers over a network. NTP can synchronize time to within milliseconds over the internet and even more precisely within local area networks. It is essential for various applications that require precise timekeeping, such as logging events, security protocols, and time-sensitive transactions.

Here are some key points about NTP:

1. **Hierarchy of Time Sources**: NTP uses a hierarchical system of time sources, with each level called a "[[Stratum]]." Stratum 0 devices are high-precision timekeeping devices like atomic clocks or GPS clocks. Stratum 1 servers are directly connected to Stratum 0 devices, and Stratum 2 servers synchronize with Stratum 1 servers, and so on.
    
2. **Accuracy and Precision**: NTP can achieve synchronization accuracy within a few milliseconds over the internet and even better in local networks.
    
3. **Algorithms**: NTP uses complex algorithms to account for variable network delays and to select the best time source from a set of available servers.
    
4. **Security**: While NTP itself is not inherently secure, there are extensions and best practices to secure NTP communications, such as using authentication mechanisms to prevent malicious time sources from disrupting synchronization.
    
5. **Implementation**: NTP is widely implemented in various operating systems and network devices. The most common implementation is the `ntpd` daemon, which runs on Unix-like systems.
    
6. **Versions**: The protocol has evolved over time, with NTPv4 being the most recent version, offering improvements in accuracy, security, and scalability over previous versions.