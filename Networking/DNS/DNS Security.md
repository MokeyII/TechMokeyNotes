---
tags:
  - Networking
---

[[DNS]] (Domain Name System) security is crucial for protecting the integrity and confidentiality of [[DNS]] data and ensuring the reliability of internet services. Here are some key [[DNS]] security mechanisms and protocols:
![[DoH and DoT.png]]
###  DNSSEC (Domain Name System Security Extensions):
- **Purpose**: Adds a layer of security to prevent certain types of attacks, such as cache poisoning and man-in-the-middle attacks.
- **How it Works**: Uses digital signatures to ensure that the [[DNS]] responses are authentic and have not been tampered with. It provides data integrity and origin authentication.

### DNS over HTTPS (DoH):
- **Purpose**: Encrypts [[DNS]] queries to improve privacy and security.
- **How it Works**: Sends [[DNS]] queries and responses over HTTPS, making it difficult for eavesdroppers to see what websites a user is trying to access.

### DNS over TLS (DoT):
- **Purpose**: Similar to DoH, it aims to encrypt [[DNS]] queries to protect user privacy.
- **How it Works**: Uses TLS (Transport Layer Security) to encrypt [[DNS]] queries and responses, ensuring that the communication between the client and the [[DNS]] server is secure

### DNSCrypt:
- **Purpose**: Encrypts [[DNS]] traffic between the user's device and the [[DNS]] resolver.
- **How it Works**: Uses cryptographic signatures to verify that responses come from the chosen [[DNS]] resolver and have not been tampered with.

### DANE (DNS-based Authentication of Named Entities):
- **Purpose**: Provides a way to authenticate TLS certificates using DNSSEC.
- **How it Works**: Stores TLSA (Transport Layer Security Authentication) records in [[DNS]], which can be used to verify the authenticity of TLS certificates.

### Response Policy Zones (RPZ):
- **Purpose**: Allows [[DNS]] administrators to enforce custom rules for [[DNS]] responses.
- **How it Works**: Uses specially configured [[DNS]] zones to block, redirect, or modify [[DNS]] responses based on policies set by the administrator.

### DNS Filtering:
- **Purpose**: Blocks access to malicious or unwanted domains.
- **How it Works**: Uses lists of known malicious domains to filter out harmful [[DNS]] queries, preventing users from accessing dangerous sites.

### DNS Tunneling Detection:
- **Purpose**: Detects and prevents the use of [[DNS]] for tunneling other types of traffic, which can be used for data exfiltration or bypassing network controls.
- **How it Works**: Monitors [[DNS]] traffic for patterns indicative of tunneling and takes action to block or alert on suspicious activity.

### Anycast Routing for DNS:
- **Purpose**: Enhances the availability and resilience of [[DNS]] services.
- **How it Works**: Uses multiple geographically distributed servers with the same IP address to provide redundancy and load balancing for DNS queries.

### DNS Rate Limiting:
- **Purpose**: Mitigates the impact of [[DNS]]-based DDoS (Distributed Denial of Service) attacks.
- **How it Works**: Limits the rate of [[DNS]] queries from a single source to prevent abuse and reduce the load on [[DNS]] servers.

Implementing these [[DNS]] security measures can significantly enhance the security and reliability of [[DNS]] infrastructure, protecting against a wide range of threats and vulnerabilities.
