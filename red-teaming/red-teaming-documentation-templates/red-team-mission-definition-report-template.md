# Red Team Mission Definition Report Template

## 1. Red Team Mission Definition

***

### 1.1. Mission Name

Active Directory Assessment - Internal Network

### 1.2. Type of Mission

Full-Scope

### 1.3. Objective of Mission

The primary objective of this Red Team mission is to assess the security of Company Inc.'s internal network, with a specific focus on the Active Directory infrastructure. The mission aims to identify vulnerabilities, misconfigurations, and potential weaknesses that could be exploited by malicious actors. By simulating real-world attacks, we will evaluate the organization's readiness to defend against advanced threats.

### 1.4. Scope of Mission

The scope of this mission includes the following:

* Assessment of the Active Directory infrastructure, including domain controllers, user accounts, and group policies.
* Identification of security weaknesses in the internal network architecture.
* Limited social engineering tests on selected employees.
* No physical intrusion or damage to systems is allowed.
* All testing activities will be conducted within agreed-upon business hours.

## 2. Definition of the Mission

***

### 2.1. Scenario 1: Active Directory Enumeration

#### Objective

* The objective of this scenario is to enumerate the Active Directory environment to gather information about domain controllers, user accounts, and group policies.

#### Description

* The Red Team will use open-source and custom tools to gather information about the Active Directory structure and user accounts.
* The goal is to create a detailed map of the AD environment.

#### Flags

* Successful enumeration of domain controllers and administrative accounts.
* Discovery of group policies that may be vulnerable to exploitation.

#### Operations: Initial Point

* The Red Team will initiate this scenario by gaining access to a compromised internal workstation.

#### Attacker

* Red Team Member: John Smith

#### Location

* The operation will take place within the Company Inc. internal network.

#### Initial Information

* No specific initial information is available for this scenario.

#### Limitations

* No attempts to exploit vulnerabilities or escalate privileges during this scenario.
* No sensitive data extraction or data manipulation.
