# NIST CSF Incident Report Analysis — ICMP Flood DoS Attack

## Repository Description

NIST Cybersecurity Framework (CSF) incident report analyzing an ICMP flood denial-of-service attack, including identification, protection, detection, response, and recovery planning.

---

## Overview

This repository documents a simulated cybersecurity incident involving a multimedia company that experienced a network outage caused by a flood of incoming **ICMP packets**.

The incident affected the organization’s internal network for approximately two hours. During the attack, normal internal traffic could not access network resources because the network was overwhelmed by ICMP traffic entering through an unconfigured firewall.

The incident is analyzed using the five core functions of the **NIST Cybersecurity Framework (CSF)**:

1. Identify
2. Protect
3. Detect
4. Respond
5. Recover

> **Terminology note:** The activity scenario describes the event as a **DoS attack**, while the supplied exemplar labels it a **DDoS attack**. This report follows the scenario’s wording and refers to it as an **ICMP flood DoS attack**, since the scenario identifies a malicious actor but does not establish multiple distributed attacking sources.

---

# Summary

The company experienced a cybersecurity incident when its network services suddenly stopped responding because of a large flood of incoming ICMP packets.

The attack entered through an **unconfigured firewall**, allowing the malicious traffic to overwhelm the internal network. As a result, normal internal network traffic could not access network resources for approximately two hours.

The incident management team responded by:

- Blocking incoming ICMP packets
- Taking non-critical network services offline
- Restoring critical network services

Following the incident, the cybersecurity team determined that the firewall configuration allowed the ICMP flood to enter the network.

The network security team then implemented:

- A firewall rule to limit the rate of incoming ICMP packets
- Source IP address verification to detect spoofed IP addresses
- Network monitoring software to identify abnormal traffic patterns
- IDS/IPS controls to filter suspicious ICMP traffic

---

# Identify

The incident was an **ICMP flood denial-of-service (DoS) attack** targeting the company’s internal network.

The malicious actor generated enough ICMP ping traffic to overwhelm network resources and prevent legitimate users from accessing network services.

## Systems and Resources Affected

The incident affected:

- The internal network
- Critical network services
- Non-critical network services
- Firewall-protected network resources
- Normal internal network communications

## Root Cause

The key security weakness was an **unconfigured firewall** that did not adequately control incoming ICMP traffic.

## Risks Identified

- Excessive ICMP traffic
- Missing ICMP rate limiting
- Inadequate firewall filtering
- Potential spoofed source IP addresses
- Limited detection of abnormal network behavior

---

# Protect

The organization should implement safeguards to reduce the likelihood and impact of similar incidents.

## Firewall Rate Limiting

A firewall rule should limit the rate of incoming ICMP packets.

This reduces the ability of an attacker to overwhelm the network with excessive ping traffic.

```text
External ICMP Traffic
        |
        v
     Firewall
        |
        v
 ICMP Rate Limiting
        |
    +---+---+
    |       |
 Allowed  Excessive
 Traffic   Traffic
    |       |
    v       v
 Network   Blocked
```

## IDS/IPS

An **Intrusion Detection and Prevention System (IDS/IPS)** should inspect ICMP traffic for suspicious characteristics.

The IDS/IPS can help identify or block traffic patterns associated with flooding attacks.

## Firewall Configuration Review

Firewall rules should be reviewed regularly to ensure:

- ICMP traffic is appropriately restricted
- Unnecessary traffic is denied
- Rules reflect current network requirements
- Security controls remain effective after changes

---

# Detect

The organization should continuously monitor network activity to identify suspicious traffic before it causes a major outage.

## Source IP Address Verification

The firewall should verify incoming source IP addresses to identify potentially spoofed traffic.

This helps detect packets that appear to originate from false or unauthorized sources.

## Network Monitoring

Network monitoring software should be used to detect:

- Sudden spikes in ICMP traffic
- Unusual traffic volume
- Repeated ping requests
- Traffic from unexpected sources
- Abnormal network behavior

## IDS/IPS Monitoring

The IDS/IPS can generate alerts or block traffic that matches suspicious ICMP patterns.

## Detection Flow

```text
Incoming Network Traffic
          |
          v
       Firewall
          |
          v
Source IP Verification
          |
          v
Network Monitoring
          |
          v
       IDS/IPS
          |
     +----+----+
     |         |
 Normal     Suspicious
 Traffic      Traffic
     |         |
     v         v
 Allowed    Alert/Block
```

---

# Respond

For future incidents, the cybersecurity team should follow a structured response process.

## 1. Contain the Incident

- Block or rate-limit malicious ICMP traffic
- Isolate affected systems when necessary
- Disable non-critical network services
- Preserve critical business services where possible

## 2. Analyze the Incident

The team should review:

- Firewall logs
- IDS/IPS alerts
- Network monitoring data
- Traffic patterns
- Source IP information
- System and network logs

## 3. Neutralize the Threat

The organization should:

- Update firewall rules
- Block confirmed malicious sources
- Apply ICMP rate limits
- Verify anti-spoofing controls
- Tune IDS/IPS rules

## 4. Communicate

The incident should be reported to:

- IT and cybersecurity teams
- Management
- Relevant stakeholders
- Legal or regulatory authorities when applicable

## 5. Improve Procedures

After the incident, the organization should review what worked and what failed, then update:

- Firewall configurations
- Incident response procedures
- Monitoring thresholds
- Escalation procedures
- Recovery documentation

---

# Recover

Recovery should focus on restoring network services in a controlled order.

## Recovery Sequence

1. Confirm that malicious ICMP traffic has been blocked or reduced.
2. Keep non-critical services offline temporarily to reduce internal traffic.
3. Restore critical network services first.
4. Verify that critical resources are stable and accessible.
5. Monitor the network for continued abnormal traffic.
6. Restore non-critical services after the threat has subsided.
7. Confirm that normal network operations have resumed.

```text
Attack Contained
      |
      v
Critical Services Restored
      |
      v
Network Stability Verified
      |
      v
Continued Monitoring
      |
      v
Non-Critical Services Restored
      |
      v
Normal Operations
```

---

# NIST CSF Mapping

| NIST CSF Function | Application to This Incident |
|---|---|
| **Identify** | Determine the ICMP flood attack, affected network resources, and firewall weakness |
| **Protect** | Apply ICMP rate limiting, firewall rules, and IDS/IPS filtering |
| **Detect** | Use source IP verification, monitoring tools, and IDS/IPS alerts |
| **Respond** | Contain traffic, isolate resources, analyze logs, communicate, and improve procedures |
| **Recover** | Restore critical services first and return remaining systems to normal operation |

---

# Incident Timeline

```text
Unconfigured Firewall
        |
        v
ICMP Flood Enters Network
        |
        v
Internal Network Overwhelmed
        |
        v
Network Services Stop Responding
        |
        v
Incoming ICMP Blocked
        |
        v
Non-Critical Services Taken Offline
        |
        v
Critical Services Restored
        |
        v
Security Investigation
        |
        v
New Controls Implemented
```

---

# Security Controls Implemented

| Security Control | Purpose |
|---|---|
| ICMP rate limiting | Reduces excessive incoming ICMP traffic |
| Source IP verification | Helps detect spoofed IP addresses |
| Network monitoring | Detects abnormal traffic patterns |
| IDS/IPS | Filters and alerts on suspicious ICMP traffic |
| Firewall rule review | Ensures traffic filtering remains effective |

---

# Key Findings

- The incident was caused by a flood of incoming ICMP packets.
- The internal network became unavailable to normal traffic.
- The outage lasted approximately two hours.
- An unconfigured firewall allowed the attack traffic to enter.
- Blocking ICMP traffic helped contain the incident.
- Non-critical services were taken offline to reduce network load.
- Critical services were restored first.
- ICMP rate limiting was added to the firewall.
- Source IP verification was implemented.
- Network monitoring and IDS/IPS controls were added.
- The NIST CSF provides a structured approach for improving security after the incident.

---

# Skills Demonstrated

This activity demonstrates understanding of:

- NIST Cybersecurity Framework
- Incident response
- Network security
- ICMP
- DoS analysis
- Firewall configuration
- IDS/IPS
- Network monitoring
- Source IP verification
- Traffic filtering
- Incident containment
- Recovery planning
- Security documentation

---

# Repository Purpose

This repository is maintained as part of a cybersecurity learning and professional portfolio.

It demonstrates the ability to:

- Analyze a network security incident
- Apply the NIST CSF
- Identify affected systems and root causes
- Recommend protective controls
- Define detection methods
- Develop a response plan
- Create a recovery strategy

---

# Disclaimer

This repository documents a simulated cybersecurity training scenario and is intended for educational and portfolio purposes.

---

## Suggested GitHub Topics

`cybersecurity` `nist-csf` `incident-response` `network-security` `icmp` `dos` `firewall` `ids` `ips` `network-monitoring` `risk-management`

## Keywords

`Cybersecurity` `NIST CSF` `ICMP Flood` `DoS Attack` `Incident Response` `Firewall` `IDS/IPS` `Network Monitoring` `Source IP Verification` `Recovery Planning`
