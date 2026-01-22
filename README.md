
# Securing Departmental Access with Extended ACLs

This project demonstrates the design and implementation of a secure departmental network using Cisco Packet Tracer. The network simulates a corporate environment with two departments — Human Resources (HR) and Finance — and enforces controlled access to internal services using Extended Access Control Lists (ACLs).

The primary security objective was to allow both departments access to shared services such as DHCP, DNS, and HTTP, while restricting Finance department access to an internal file server.

---

## Project Scope

- Designed a multi-segment network topology
- Configured routing between departmental networks
- Deployed centralized DHCP and DNS services
- Hosted a web server accessible to both departments
- Implemented FTP services with access restrictions
- Applied Extended ACLs to enforce security policies
- Validated network functionality through testing

---

## Network Design Overview

The network follows a hierarchical structure:

- Two departmental LANs (HR and Finance)
- A centralized router providing inter-network routing
- Dedicated servers for DHCP, DNS, Web (HTTP), and File Transfer (FTP)
- Switches connecting end devices within each department

Each department was assigned a separate subnet. The router was configured as the default gateway for both networks and used as the enforcement point for access control policies.

---

## My Contribution (Group Project)

This was a collaborative group project. My individual contributions included:

- Router configuration and interface setup  
- DHCP relay configuration using IP helper addresses  
- DHCP server setup and address pool configuration  
- Authoring the technical documentation for:
  - Router configuration  
  - DHCP configuration  
  - DNS configuration  
  - Web server configuration  

---

## Router Configuration

The router served as the central connectivity device between the HR and Finance departments.

- Interface Gig0/0/0 (HR): 192.168.5.1/24  
- Interface Gig0/0/1 (Finance): 192.168.6.1/24  

To support centralized DHCP services, an IP helper address was applied to the HR-facing interface to forward broadcast DHCP requests to the DHCP server located in the Finance subnet.

This configuration ensured that client devices in both departments could obtain IP addresses dynamically.

---

## DHCP Server Configuration

A dedicated DHCP server was deployed in the Finance network and assigned a static IP address.

Key configuration steps:

- Enabled DHCP services  
- Created a DHCP address pool  
- Configured subnet mask and default gateway  
- Set DNS server IP for name resolution  

Dynamic IP assignment was validated by configuring client devices to obtain addresses automatically.

---

## DNS and Web Server Configuration

A DNS server was configured to provide name resolution services for all devices.

- Created a forward lookup record mapping `www.podvega.com` to the web server IP  
- Verified resolution from both departmental networks  

A web server was deployed to host the company website and provide HTTP services.

Successful access to the website from both HR and Finance confirmed:

- Proper DNS resolution  
- Inter-network routing  
- Web service availability  

---

## File Server and Access Control

A file server was configured to provide FTP services.

- Enabled FTP services  
- Created user accounts  
- Stored sample files  

Before applying access restrictions, both departments were able to access the file server.

An Extended ACL was implemented on the router to restrict FTP access from the Finance subnet while allowing HR access.

Key ACL logic:

- Permit HR subnet FTP traffic (TCP ports 20 and 21)  
- Deny Finance subnet FTP traffic  
- Allow all other required services (DNS, HTTP, DHCP)

---

## Network Testing

Validation steps included:

- Verifying dynamic IP assignment via DHCP  
- Confirming DNS name resolution  
- Testing HTTP access from both departments  
- Testing FTP access before and after ACL application  
- Confirming Finance access was blocked while HR retained access  

---

## Tools and Technologies

- Cisco Packet Tracer  
- Router and switch configuration  
- DHCP and DNS services  
- FTP and HTTP services  
- Extended Access Control Lists (ACLs)  
- IP routing and subnetting  

---

## What I Learned

- Designing segmented networks for departmental isolation  
- Configuring routers as centralized control points  
- Implementing centralized DHCP services  
- Applying Extended ACLs to enforce security policies  
- Testing and validating access controls  
- Documenting technical configurations clearly  

---

## Acknowledgment

This project was completed as part of a group collaboration. All team members contributed to the overall design and implementation. My contributions focused on router configuration, DHCP services, and technical documentation for core network services.

---

## Screenshots and Configuration Files

Screenshots and Packet Tracer files are included in this repository to demonstrate the network topology, configurations, and testing results.
