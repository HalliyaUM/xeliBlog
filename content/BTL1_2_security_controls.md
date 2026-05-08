---
title: BTL1 Notes 2 Security Controls
tags:
  - BTL1
---
# Security Fundamentals; Security Controls


#### Physical Security

to prevent unauthorised access to a building, or areas within to make intrusion as hard as possible.

**3 main controls**
- deterrents (e.g. warning sings, CCTV, fences, guard dogs, security lighting)
- monitoring controls (e.g. CCTV, fences, Security guards, IDS)
- access controls (e.g. RFID badges, keys)
tldr; literally what my uni security does


#### Endpoint security

- HIDS; Host Intrusion Detection Systems
	- sw installed on an endpoint - allows for the detection of suspivious/malicious activity using rules (to see if anything matches known malicious patterns)
- HIPS; Host Intrusion Prevention Systems
	- sw installed on an endpoint as well - similar to HIDS but is able to take autonomous actions to defend system once the malicious activity has been detected
	- Rules contains actions here, where HIDS only contains pattern
		- e.g. terminating connections to websites or IP addresses, deleting malicious files, generating an alert.
- AV; Anti-virus software
	- *should* be deployed on all endpoints (e.g. desktops, laptops, and servers)
	- to detect & remove known malware that is present on the system

	 **Two types of AV**
	- Signature based
		- specific patterns of activity to identify previously documented malware, either removing the file, generating an alert, or quarantining the malware
	- Behaviour based
		- identify suspicious behavior by creating a baseline of "normal" activity and working to identify any deviations or anomalies that don't fit the baseline, as these could indicate suspicious or malicious activity.
- Log Monitoring




#### Email Security 

- Spam filter
	- piece of sw that scans incoming emails to see if they have telltale signs of spam or malicious emails
- DLP; Data loss prevention
	- prevent sensitive business or personal information from leaving the organization in an unauthorized manner
	- Email specifically, it can monitor outgoing emails at different levels (e.g. email body content, headers, or attachment of various types)
	- If DLP solution deems important information is about to be sent out of the organisation, these emails will not make it past the email gateway
		- it can be scanned for specific keywords, regex queries to flag messages containing certain content.
	- If not email, 
		- data fingerprint (all confidential file have fingerprint and DLP software will scan the fingerprint of fingerprint of sent file and compare)
		- Matching keywords (Regex etc)
		- Pattern match (this regex too? e.g. say if HTTP response has 16 integers, DLP sytem will think this is high likely to be credit card number, and protect this number as personal information)
		- Hash comparison etc
- Email scanning
	- Typically phishing emails will contain either a malicious URL or a malicious attachment (or both lol) 
	  ➡️ specially designed scanners will read email header & body 
	  ➡️ work to identify malicious indicators either using pattern | signatures | blacklists (includes lists of known malicious email senders, file hashes, and domain names)
	- suspicious email has been detected 
	  ➡️ quarantined so it's not delivered to an employee mailbox 
	  ➡️ alert is generated to inform the security team to investigate
- Security awareness training


#### Network Security
🔥 
	I thought HIDS meant IDS that I learnt from Network security but NO!! HIDS != NIDS
	HIDS works on host by installing agent (gathers logs, checks file integrity, looks over processes and analysis based on rules.)
	e.g. if system file changes ➡️ suspicious for rootkit, if system file changes ➡️ risk of privilege escalation

- Network Intrusion Detection Systems; NIDS
	- can come in the form of 1️⃣ software, 2️⃣ physical devices that monitors network traffic in order to generate alerts for human analysts to investigate
	- #TODO:Can be positioned in 🚩
		- **Inline**; NIDS is sitting directly in the path of network traffic, meaning *all traffic will pass through the NIDS*
		- **Network Tap**; will be connected to the network by tapping into a physical connection, such as cable
		- **Passive**; is connected to a SPAN port on a network device. This physical port allows all traffic passing thought the device to be mirrored to the SPAN port, so NIDS will get a copy of all network activity 
	- Purpose: generate alerts so that human analysts can investigate and take action if needed.

- Network Intrusion Prevention Systems; NIPS
	- can take actions :X
#TODO: Read https://www.geeksforgeeks.org/computer-networks/difference-between-hids-and-nids/

- Firewalls 🚩
	- used to seperate parts of a network to create private zones by restricting the traffic that can come in or go out
	#TODO: Read https://co-no.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EB%B0%A9%ED%99%94%EB%B2%BDFirewall
	**Three different types of Firewall**
	- Standard firewalls run on dedicated hardware and sit at key points of the network.
	- Local firewalls in software form run on endpoints (such as Windows firewall).
	- Web application firewalls in software form sit on internet-facing web servers that host websites or web applications.

- Log Monitoring
	- Network devices can generate logs ➡️ can be sent to a SIEM platform
	- SIEM provides dashboard that analysts can utilise to monitor activity & respond to alerts
	- Network devices can provide very valuable information such as...
		- Web Proxy logs
			- this devices processes web-based request to the internet, and will contain list of sites visited by employees ➡️ can be combined with a blacklist to generate SIEM alerts when an employee tries to visit a malicious website or explicit website
		- Perimeter firewalls 🚩
			- If malicious actor starts port scanning the org & requests from the scanning IP(s) smashes ➡️ the perimeter firewalls picks this activity up ➡️ sending this to SIEM, an alert can be generated when a port/vuln scanning is being conducted or DDoS starts

- NAC; Network Access Control
	- prevent rogue or non-compliant devices from connecting to a private network
	- NAC can enforce to devices 
		- to have latest patches and security updates
		- must be running anti-virus.
	- by not letting devices connect to the network until they have met all of the requriements
	- typically for BYOD or guest networks, where non-corporate devices will be connecting
	- Ever been to a restaurant or **shopping centre that offers free wifi, but you need to sign up?** That's NAC in action, allowing the network administrators to restrict access and manage sessions, such as networks that have time limits, like public transport and commercial flights.



#### AAA Control Methods

**AAA for...**
Authentication
Authorisation
Accountability


- Authentication
	- involves using some form of verification to confirm that the identity is correct
	- Three different types of authentication
		1. Something you know
			"a.k.a. Authentication by knowledge"
			proving your identity using something that you can remember (e.g. PIN code, password, security questions)
		2. Something you have
			"a.k.a. Authentication by ownership"
			proving your identity with a physical item that you have with you (e.g. ID, set of keys)
		3. Something you are
			"a.k.a. Authentication by the characteristic"
			hardest controls to bypass since it directly associated with an individual (e.g. biometric systems, fingerprints, retinal scans, face identification)

		**We need combination of at least 2, preferably 3 ➡️ implying multi-factor**
		
- Authorisation
	- all about what authenticated user is permitted to do
	- Using the **Principle of Least Privilege**, we always want to give individuals only the access they require to complete their job, and nothing more.

- Accountability
	- the process of being able to identify what has happened & when which can be used as evidence during a security event or incident.
	- Accountability helps to validate what happened, by who, and in some cases can help to uncover if this was actually the individual or if someone else used this identity to conduct malicious actions.


