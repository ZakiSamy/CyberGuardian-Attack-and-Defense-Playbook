# Web Protection & Security



## Web Application Firewall (WAF)

***

A Web Application Firewall (WAF) is a vital security tool designed to monitor, filter, and block incoming and outgoing data packets for web applications and websites. Deployed in various forms, including host-based, network-based, or cloud-based solutions, WAFs are typically integrated through reverse proxies and positioned in front of one or multiple applications or websites. Their primary purpose is to analyze incoming web traffic, identify suspicious or malicious requests, and safeguard against common web application attacks. Here's a closer look at WAFs, their types, and security models:

### Overview

***

* **Function**: WAFs analyze web traffic, identifying and blocking potentially harmful requests.
* **Protection**: Mitigates web application attacks like SQL injection, cross-site scripting, and buffer overflows.
* **Enforcement**: Enforces security policies, including authentication and access control.
* **Compliance**: Helps ensure data security and compliance with regulations like GDPR and PCI-DSS.

### Types of WAF

***

#### 1. Network-based WAF

* **Deployment**: Installed in front of a web application, intercepting traffic before it reaches the application.
* **Functionality**: Monitors and filters traffic at the network level to protect the application.

#### 2. Host-based WAF

* **Deployment**: Installed on the same server as the web application, offering local traffic analysis and protection.
* **Functionality**: Analyzes traffic locally on the server, providing tailored security for the specific application.

#### 3. Cloud-based WAF

* **Deployment**: Offered as a service by cloud providers, safeguarding web applications hosted in the cloud.
* **Functionality**: Leverages cloud infrastructure to provide scalable, cloud-native security.

### Security Models

***

#### 1. Positive Security Model

* **Approach**: Allows only traffic explicitly defined in the security policy.
* **Pros**: Provides a strict and secure environment by permitting only whitelisted traffic.
* **Cons**: Requires constant updating of policies as legitimate traffic changes.

#### 2. Negative Security Model

* **Approach**: Blocks traffic matching known attack patterns while allowing all other traffic.
* **Pros**: Effective at identifying and blocking known threats.
* **Cons**: May allow new, unknown threats to pass through.
