---
title: BTL1 Notes Week 1-2 Security Controls
tags:
  - BTL1
---
# Security Fundamentals; Security Controls


#### Physical Security

to prevent unauthorised access to a building, or areas within to make intrusion as hard as possible.

**3 main controls**
- deterrents (e.g. warning sings, CCTV, fences, guard dogs, security lighting)
- monitoring controls (e.g. CCTV, Security guards, IDS)
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
  