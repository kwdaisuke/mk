### Network protocol
#### TCP/IP (Transmission Control Protocol/Internet Protocol): 
This is the most widely-used network protocol suite, and it is the foundation of the internet. It is responsible for routing packets of data between devices, and it includes a number of different protocols such as HTTP, FTP, and DNS.

#### HTTP (Hypertext Transfer Protocol): 
This is the protocol used for transferring web pages and other data over the internet. It is based on the request-response model, where a client (such as a web browser) sends a request to a server, and the server responds with the requested data.

#### FTP (File Transfer Protocol): 
This is a standard protocol for transferring files between computers on a network. It allows users to upload and download files, and it also provides features such as file management and security.

#### DNS (Domain Name System): 
This is a distributed system that translates domain names (such as www.google.com) into IP addresses. It is responsible for resolving domain names to IP addresses so that users can access the correct website.

#### DHCP (Dynamic Host Configuration Protocol): 
This is a protocol used to dynamically assign IP addresses to devices on a network. DHCP servers assign IP addresses to clients automatically, and they also provide other network configuration information such as subnet mask and default gateway.

#### SNMP (Simple Network Management Protocol): 
This is a protocol used to manage and monitor network devices, such as routers and switches. It allows network administrators to retrieve information about the performance and configuration of devices, and to send commands to configure or troubleshoot them.

#### SSL/TLS (Secure Sockets Layer/Transport Layer Security):
This is a protocol used to encrypt network communications and provide secure connections. It is commonly used for secure web browsing (HTTPS) and email (SMTPS) .

### Network topology
Network topology refers to the physical and logical arrangement of devices and the connections between them on a computer network. There are several common network topologies, including:

#### Star topology: 
In a star topology, all devices are connected to a central hub or switch. This allows for easy management and isolation of individual devices, but if the central hub fails, the entire network will be down.

#### Bus topology: 
In a bus topology, all devices are connected to a single cable or bus. This is a simple and cost-effective approach, but it can be difficult to isolate and troubleshoot individual devices.

#### Ring topology: 
In a ring topology, devices are connected in a circular pattern and data travels in one direction around the ring. This allows for a dedicated path between devices, but if one device fails, the entire network can be affected.

#### Mesh topology: 
In a mesh topology, each device is connected to multiple other devices, creating multiple paths between devices. This provides redundancy and allows for continued communication even if one path is lost, but it can be more complex and expensive to set up.

#### Tree topology: 
In a tree topology, a central hub or switch is connected to multiple other hubs or switches, creating a hierarchical structure. This is commonly used in large networks, such as in a campus or enterprise environment, as it allows for easy management and scalability.

#### Hybrid topology: 
A combination of two or more of the above topologies is often used in networks where multiple types of connections are needed.

### Network security
Network security refers to the measures and technologies that are used to protect computer networks and the data they transmit from unauthorized access, use, disclosure, disruption, modification, or destruction. Some common network security measures include:

#### Firewalls: 
A firewall is a security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules. Firewalls can be hardware- or software-based, and they can be used to block unauthorized access to a network, as well as to limit the types of traffic that are allowed to pass through.

#### Intrusion detection and prevention systems (IDPS): 
An IDPS is a network security technology that monitors network traffic for signs of unauthorized access or malicious activity. It can be used to detect and prevent a wide range of attacks, such as denial of service (DoS) attacks, malware, and unauthorized access to sensitive data.

#### Virtual Private Networks (VPNs): 
A VPN is a technology that allows users to securely access a private network over the internet. It uses encryption and tunneling to create a secure connection between the user and the network, allowing for secure remote access and protecting data in transit.

#### Access controls:
Access controls are security measures that are used to regulate who is allowed to access a network and what they are allowed to do. This can include user authentication and authorization, as well as role-based access controls (RBAC) which determine what a user can do based on their role in the organization.

#### Encryption: 
Encryption is the process of converting plaintext into unreadable ciphertext, which can only be decrypted with the proper key. This can be used to protect sensitive data, both at rest and in transit.

#### Network segmentation: 
Network segmentation is the process of dividing a network into smaller subnets or segments, each with its own set of security measures. This can help to limit the spread of a security breach and make it easier to identify and isolate compromised devices.

#### Network monitoring: 
Network monitoring is the process of constantly monitoring a network for security-related events and incidents. This can include monitoring network traffic, system logs, and user activity to detect and respond to security threats.

By implementing these security measures, organizations can protect their networks and data from unauthorized access and malicious attacks, and maintain the confidentiality, integrity, and availability of their information.

### OSI (Open Systems Interconnection) model 
framework that is used to understand and describe the different layers of a networked communication system. It divides the process of communication between two systems into seven different layers, each with its own specific functions and responsibilities.

<iframe width="560" height="315" src="https://www.youtube.com/embed/LANW3m7UgWs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
The seven layers of the OSI model are:


#### Physical Layer: 
This layer is responsible for the physical transmission of data over the network, including the medium (e.g. copper wire, optical fiber) and the signaling method (e.g. voltage levels, modulation).

#### Data Link Layer: 
This layer is responsible for providing reliable communication between devices on the same local network segment by creating, maintaining, and terminating links between devices.

#### Network Layer: 
This layer is responsible for routing data packets between different networks and providing logical addressing so that devices on different networks can communicate.

#### Transport Layer: 
This layer is responsible for providing end-to-end transport of data between applications on different devices, ensuring reliable communication and error-checking.

#### Session Layer: 
This layer is responsible for establishing, maintaining, and terminating sessions between applications on different devices.

#### Presentation Layer: 
This layer is responsible for translating data between the application and network formats, and for compressing and encrypting data to protect it during transmission.

#### Application Layer: 
This layer is responsible for providing a user interface and services to applications, such as file transfer and email.

![](https://miro.medium.com/max/1400/1*-hQHFX-UjlruHDf9Je0lXg.png){: style="height:400px;width:400px"}
