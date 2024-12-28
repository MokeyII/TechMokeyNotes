---
tags:
  - Networking
---

The term "stratum" refers to the hierarchical level of a time source within the [[NTP]] network. The stratum level indicates the distance from the reference clock, with lower numbers indicating closer proximity to the reference clock. Here’s a detailed explanation of the different stratum levels:

### Stratum Levels

0. **Stratum 0**:
    
    - **Description**: These are high-precision timekeeping devices such as atomic clocks, GPS clocks, or radio clocks.
    - **Role**: They are not directly connected to the network but provide the reference time to Stratum 1 servers.
    - **Examples**: Cesium atomic clocks, GPS receivers.
1. **Stratum 1**:
    
    - **Description**: These are primary time servers directly connected to Stratum 0 devices.
    - **Role**: They distribute the reference time to lower-stratum servers.
    - **Accuracy**: Typically within microseconds to the reference clock.
    - **Examples**: Time servers at national timekeeping institutions, GPS-synchronized servers.
2. **Stratum 2**:
    
    - **Description**: These servers synchronize their time with Stratum 1 servers.
    - **Role**: They provide time to Stratum 3 servers and other clients.
    - **Accuracy**: Typically within milliseconds to Stratum 1 servers.
    - **Examples**: Organizational NTP servers that sync with public Stratum 1 servers.
3. **Stratum 3**:
    
    - **Description**: These servers synchronize their time with Stratum 2 servers.
    - **Role**: They provide time to Stratum 4 servers and other clients.
    - **Accuracy**: Typically within tens of milliseconds to Stratum 2 servers.
    - **Examples**: Departmental NTP servers within an organization.
4. **Stratum 4 and Below**:
    
    - **Description**: These servers synchronize their time with the next higher stratum level.
    - **Role**: They continue to distribute time to lower-stratum servers and clients.
    - **Accuracy**: Decreases as the stratum level increases, but still within acceptable limits for most applications.
    - **Examples**: Local network servers, individual computers.

### Key Points

- **Hierarchy**: The stratum system creates a hierarchical structure that ensures time is distributed efficiently and accurately from the most precise sources down to individual devices.
- **Redundancy**: NTP clients typically query multiple servers at different stratum levels to ensure reliability and accuracy.
- **Selection**: NTP algorithms select the best time source based on factors like stratum level, network delay, and jitter.

### Example Scenario

Imagine a corporate network where precise timekeeping is crucial:

1. **Stratum 1**: The company has a GPS-synchronized server that acts as a Stratum 1 server.
2. **Stratum 2**: Departmental servers synchronize with the Stratum 1 server.
3. **Stratum 3**: Individual workstations and other devices synchronize with the departmental servers.

This hierarchical structure ensures that all devices within the network maintain accurate and synchronized time, which is essential for logging, security, and time-sensitive applications.