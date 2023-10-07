# Cybersecurity Frameworks

## Pyramid of Pain

***

The Cybersecurity Framework “Pyramid of Pain” is a model that helps security analysts prioritize the indicators of compromise (IOCs) that they use to detect and mitigate cyberattacks. Here are some bullet points about this framework:

* The Pyramid of Pain: consists of six levels of IOCs, from the bottom to the top: hash values, IP addresses, domain names, network/host artifacts, tools, and tactics, techniques, and procedures (TTPs).
* The higher the level of IOC, the more painful it is for the attacker to change or hide it, and the more effort it takes for the analyst to find and use it.
* **Hash values:** are the easiest IOCs to use, but also the easiest for attackers to modify. They are unique identifiers of files or software that can be checked against known malicious hashes.
* **IP addresses:** are the numerical addresses of devices on the Internet. They can be used to trace the source or destination of network traffic, but they can also be spoofed or changed by attackers using proxies or VPNs.
* **Domain names:** are the human-readable names of websites or servers. They can be used to identify malicious domains that host malware or phishing pages, but they can also be registered or altered by attackers using dynamic DNS services or domain generation algorithms.
* **Network/host artifacts**: are the traces of network or host activity that indicate an attack, such as firewall logs, registry keys, or browser history. They can provide valuable context and evidence for an investigation, but they can also be deleted or modified by attackers using anti-forensics techniques.
* **Tools:** are the software or platforms that attackers use to carry out attacks, such as backdoors, password crackers, or command-and-control servers. They can reveal the capabilities and intentions of the attackers, but they can also be customized or obfuscated by attackers using encryption or packing.
* **TTPs:** are the methods and strategies that attackers use to conduct their operations, such as initial access, lateral movement, or data exfiltration. They can reveal the identity and motivation of the attackers, but they can also be adapted or diversified by attackers using different techniques or tools.

The Pyramid of Pain helps security analysts understand the trade-offs between different types of IOCs and choose the ones that will cause the most disruption and damage to the attackers. By focusing on the higher levels of the pyramid, analysts can increase their chances of detecting and mitigating cyberattacks effectivel

## Cyber Kill Chain

***

The Cybersecurity Framework “Cyber Kill Chain” is a model that describes the stages of a cyberattack and the defensive measures that can be taken to prevent or stop it. Here are some bullet points about this framework:

* The Cyber Kill Chain consists of eight phases, from the bottom to the top: reconnaissance, weaponization, delivery, exploitation, installation, command and control (C2), actions on objectives, and exfiltration.
* The lower the phase of the attack, the easier it is for the defender to detect and block it, and the less effort it takes for the attacker to execute it.
* **Reconnaissance:** is the phase where the attacker gathers information about the target, such as vulnerabilities, credentials, network architecture, or user behavior.
* **Weaponization:** is the phase where the attacker creates or modifies a malicious payload, such as malware, ransomware, or phishing email, that can exploit a vulnerability in the target system.
* **Delivery:** is the phase where the attacker sends or transfers the payload to the target system, such as via email attachment, malicious link, removable media, or network connection.
* **Exploitation**: is the phase where the payload executes on the target system and takes advantage of the vulnerability to gain access or privileges.
* **Installation:** is the phase where the payload installs additional components or tools on the target system, such as backdoors, keyloggers, or rootkits, that allow persistent access or stealthy operation.
* **Command and control (C2):** is the phase where the attacker communicates with the compromised system and directs its actions remotely, such as via a server, a domain name, or a protocol.
* **Actions on objectives:** is the phase where the attacker performs the intended goal of the attack, such as stealing data, encrypting files, destroying systems, or disrupting services.
* **Exfiltration:** is the phase where the attacker transfers the stolen data or other information from the target system to another location, such as via email, FTP, or cloud storage.

The Cyber Kill Chain helps security analysts understand and combat cyberattacks by identifying and disrupting each phase of the attack. By focusing on the higher phases of the chain, analysts can increase their chances of preventing or mitigating cyberattacks effectively.

## Unified Kill Chain

***

The Cybersecurity Framework “Unified Kill Chain” is a model that describes the 18 possible phases of a cyberattack and the defensive measures that can be taken to prevent or stop it. Here are some bullet points about this framework:

* The Unified Kill Chain consists of six phases that occur outside the defended network and 12 phases that occur within the defended network.
* The six external phases are: target selection, target identification, target reconnaissance, target vulnerability analysis, attack planning, and attack launch.
* The 12 internal phases are: initial compromise, establish foothold, escalate privileges, internal reconnaissance, move laterally, maintain presence, collect data, exfiltrate data, manipulate data, deny service, execute additional attacks, and complete mission.
* The higher the phase of the attack, the more difficult it is for the defender to detect and block it, and the more effort it takes for the attacker to execute it.
* Target selection is the phase where the attacker chooses a potential target based on their objectives, motivations, and capabilities.
* Target identification is the phase where the attacker identifies the target’s assets, such as systems, networks, or users.
* Target reconnaissance is the phase where the attacker gathers information about the target’s assets, such as vulnerabilities, configurations, or behaviors.
* Target vulnerability analysis is the phase where the attacker analyzes the information collected in the previous phase and identifies the most suitable vulnerabilities to exploit.
* Attack planning is the phase where the attacker designs and prepares a cyberattack based on the chosen vulnerabilities and objectives.
* Attack launch is the phase where the attacker initiates the cyberattack by sending or delivering a malicious payload to the target’s network or system.
* Initial compromise is the phase where the payload executes on the target’s network or system and exploits a vulnerability to gain access or privileges.
* Establish foothold is the phase where the payload installs additional components or tools on the target’s network or system that allow persistent access or stealthy operation.
* Escalate privileges is the phase where the attacker gains higher privileges on the target’s network or system by exploiting additional vulnerabilities or stealing credentials.
* Internal reconnaissance is the phase where the attacker explores the target’s network or system and discovers additional assets or information that can be used for further attacks.
* Move laterally is the phase where the attacker accesses other systems or networks within the target’s environment by exploiting vulnerabilities or using stolen credentials.
* Maintain presence is the phase where the attacker ensures continuous access to the target’s network or system by using techniques such as hiding files, modifying logs, or creating backdoors.
* Collect data is the phase where the attacker gathers data from the target’s network or system that are relevant to their objectives, such as personal information, financial records, or intellectual property.
* Exfiltrate data is the phase where the attacker transfers the collected data from the target’s network or system to another location, such as an external server, a cloud storage, or an email account.
* Manipulate data is the phase where the attacker alters or deletes data on the target’s network or system to cause damage, disruption, or deception. For example, the attacker may change financial records, erase backups, or falsify reports.
* Deny service is the phase where the attacker prevents or impairs the normal functioning of the target’s network or system by using techniques such as flooding, crashing, or encrypting. For example, the attacker may overload a server, corrupt a database, or lock a device.
* Execute additional attacks is the phase where the attacker performs other attacks on the target’s network or system or on other targets that are connected to the original target. For example, the attacker may use the compromised system as a launchpad for further attacks, or spread malware to other systems or networks.
* Complete mission is the phase where the attacker achieves their final objectives and terminates the cyberattack. For example, the attacker may demand a ransom, claim credit for the attack, or erase their traces.

The Unified Kill Chain helps security analysts understand and combat cyberattacks by identifying and disrupting each phase of the attack. By focusing on the lower phases of the chain, analysts can increase their chances of preventing or mitigating cyberattacks effectively.

## Diamond Model

***

The Cybersecurity Framework “Diamond Model” is a model that helps security analysts identify and analyze the key aspects and relationships of a cyberattack. Here are some bullet points about this model:

* The Diamond Model consists of four core features of any cyberattack: adversary, capability, infrastructure, and victim. These features are connected by edges that represent their underlying relationships and arranged in the shape of a diamond, giving the model its name.
* The adversary is the person or group that initiates and conducts the cyberattack, such as a hacker, a criminal organization, or a nation-state. The adversary has certain objectives, motivations, and capabilities that influence their actions and choices.
* The capability is the tool or technique that the adversary uses to carry out the cyberattack, such as malware, ransomware, phishing, or brute force. The capability exploits a vulnerability or weakness in the target system or network.
* The infrastructure is the physical or logical communication structure that the adversary uses to deliver or execute the capability, such as an IP address, a domain name, an email account, or a server. The infrastructure can be owned or controlled by the adversary or compromised from a third party.
* The victim is the target of the cyberattack, such as a person, an organization, or an asset. The victim suffers some impact or damage from the cyberattack, such as data theft, encryption, destruction, or disruption.
* The Diamond Model helps security analysts understand and combat cyberattacks by identifying and documenting each feature and their relationships for each event. An event is a time-bound activity where the adversary uses a capability over an infrastructure against a victim with a given result. By analyzing multiple events and linking them into activity threads, analysts can gain insights and knowledge about the adversary’s behavior, tactics, techniques, and procedures (TTPs).
* The Diamond Model also provides a framework and process for collecting, processing, analyzing, and disseminating threat intelligence. By using various data sources and analytical methods, analysts can assign confidence values to each feature and edge of the diamond and share their findings with other stakeholders.

## MITRE ATT\&CK

***

The Cybersecurity Framework “MITRE ATT\&CK” is a model that describes the common tactics, techniques, and procedures (TTPs) that cyber adversaries use to compromise and exploit their targets. Here are some bullet points about this framework:

* MITRE ATT\&CK stands for Adversarial Tactics, Techniques, and Common Knowledge. It is a globally accessible knowledge base of observed adversary behaviors based on real-world observations.
* MITRE ATT\&CK covers different domains of cyberattacks, such as enterprise, mobile, cloud, and industrial control systems (ICS). Each domain has its own matrix of tactics and techniques that represent the different phases and methods of an attack.
* A tactic is a high-level objective or goal that an adversary wants to achieve, such as initial access, persistence, or exfiltration. A technique is a specific action or method that an adversary uses to accomplish a tactic, such as phishing, registry run keys, or data encrypted for impact.
* A technique may have one or more sub-techniques that provide more details or variations of how the technique can be implemented. For example, the technique “Spearphishing Attachment” has sub-techniques such as “Malicious Excel Macro” or "Malicious Word Document".
* Each technique has a unique identifier, a description, a list of data sources that can be used to detect or prevent it, a list of platforms that it affects, a list of permissions required to execute it, a list of mitigations that can be applied to counter it, and a list of related techniques.
* Each technique also has a list of software and groups that are known to use it. Software refers to the tools or malware that implement the technique, such as Emotet or TrickBot. Groups refer to the threat actors or organizations that employ the technique, such as APT28 or Lazarus Group.
* MITRE ATT\&CK helps security analysts understand and combat cyberattacks by providing a common language and framework to describe and analyze adversary behaviors. It also helps security teams assess their defenses and identify gaps or weaknesses in their security posture.
