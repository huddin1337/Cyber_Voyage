Recently, I enrolled in the TryHackMe SOC Level 1 room, which introduces core concepts and frameworks used in cybersecurity defense. These frameworks provide a structured way to understand, detect, and respond to cyber threats. Some of the most important models covered include the Pyramid of Pain, Cyber Kill Chain, Unified Kill Chain, Diamond Model, and MITRE ATT&CK. Each framework plays a role in helping defenders think like attackers while building effective defense strategies.

# 🛡️|Cyber Defence Frameworks

1. Pyramid of Pain

* Developed by David Bianco, this model shows how difficult it is for adversaries to change certain indicators of compromise (IOCs).

* The pyramid ranges from the easiest things to change (hash values, IP addresses) to the hardest (tools, tactics, techniques, and procedures—TTPs).

* The higher up the pyramid defenders can detect and respond, the more pain they cause attackers, forcing them to adapt significantly.

2. Cyber Kill Chain

* Created by Lockheed Martin, this model breaks down an attack into seven stages: Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command & Control (C2), and Actions on Objectives.

* It’s primarily attacker-focused, showing defenders where in the chain they can intervene to stop an attack before it succeeds.

3. Unified Kill Chain

* An evolution of the traditional kill chain, combining Lockheed Martin’s Cyber Kill Chain with MITRE’s ATT&CK framework.

* Provides a more comprehensive view of both initial intrusion and post-exploitation activities, helping analysts see how modern attacks unfold end-to-end.

4. Diamond Model of Intrusion Analysis

* Focuses on analyzing intrusions through four key features: Adversary, Infrastructure, Capability, and Victim.

* By mapping these elements, defenders can better understand relationships between attackers, their tools, and their targets.

* Often used in threat intelligence to track adversary behaviors and connect multiple incidents.

5. MITRE ATT&CK Framework

* A globally used knowledge base of adversary tactics, techniques, and procedures (TTPs).

* Provides defenders with a common language for describing attacker behavior.

* Used for threat hunting, red/blue team exercises, SOC playbook development, and detection engineering.

## Summary
Together, these frameworks form the foundation of modern cyber defense. They help SOC analysts not only detect and respond to attacks but also anticipate how adversaries might adapt. From the Pyramid of Pain’s focus on attacker cost, to the tactical guidance of MITRE ATT&CK, these models give a structured way to defend networks, investigate incidents, and continuously improve security posture.

# ⚔️|Cyber Threat Intelligence
In the context of Cyber Threat Intelligence (CTI), there are several widely used tools and technologies that help analysts detect, analyze, and share threat information. Three of the most important are YARA, OpenCTI, and MISP.

1. YARA

* Known as the “pattern-matching Swiss knife” for malware research.

* Used to identify and classify malware by creating rules based on textual or binary patterns.

* Helps analysts detect known malware families, discover variants, and automate threat hunting.

* Commonly integrated into SOC workflows for scanning files, memory, or network traffic.

2. OpenCTI (Open Cyber Threat Intelligence Platform)

* An open-source platform designed to manage, store, and share structured threat intelligence.

* Supports integration with frameworks like MITRE ATT&CK, making it easier to link observed TTPs to real-world adversary behavior.

* Allows collaboration between teams by providing a knowledge base of indicators, attack campaigns, and threat actor profiles.

* Useful for building long-term intelligence analysis rather than just reactive detection.

3. MISP (Malware Information Sharing Platform & Threat Sharing)

* A community-driven platform for collecting, storing, and sharing Indicators of Compromise (IOCs) and threat intelligence.

* Enables organizations to exchange actionable intelligence in structured formats (like STIX, OpenIOC, etc.).

* Supports automation with feeds, correlation features, and sharing groups, making it valuable for collaborative defense.

* Widely adopted by governments, SOCs, and CERT/CSIRTs for real-time intel exchange.

## Summary

* YARA helps with detection and classification of malware.

* OpenCTI organizes and contextualizes threat intelligence for analysis.

* MISP facilitates the sharing and exchange of intelligence across communities.

Together, these tools strengthen CTI by covering detection, knowledge management, and collaboration — enabling defenders to stay ahead of evolving threats.
