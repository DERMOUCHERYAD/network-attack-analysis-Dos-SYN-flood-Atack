# Network Attack Analysis: DoS SYN Flood

## Introduction

This repository provides a detailed analysis of a network attack scenario, specifically focusing on a Denial of Service (DoS) attack involving a SYN Flood. The analysis is based on a cybersecurity incident report and a Wireshark capture of network traffic. This project aims to help users understand the nature of SYN Flood attacks, how to analyze them, and potential ways to prevent such attacks in the future.

## Scenario

In the given scenario, a website is experiencing connectivity issues characterized by frequent connection timeout errors. An investigation into the network traffic reveals a potential SYN Flood attack. This type of attack is designed to overwhelm a server with excessive SYN packets, disrupting legitimate user access to the site.

## Problem Description

### Symptoms

- The website intermittently fails to load and users receive connection timeout errors.
- The web server's response to genuine connection attempts is delayed or nonexistent.

### Analysis

#### 1. Understanding SYN Flood Attacks

A SYN Flood attack exploits the TCP three-way handshake process:

1. **SYN Packet**: The attacker sends a high volume of SYN packets, initiating connection requests.
2. **SYN-ACK Packet**: The server responds to each SYN with a SYN-ACK packet, reserving resources for each request.
3. **ACK Packet**: The attacker does not complete the handshake by sending the final ACK packet, leaving the connections half-open.

This flood of incomplete connections exhausts server resources, preventing it from processing legitimate connection requests.

#### 2. Analyzing the Attack

**Wireshark Analysis**: By examining the provided `Wireshark TCP_HTTP` capture file, you can identify the following patterns:

- **Red vs. Green Columns**: Malicious SYN requests are highlighted in red, while legitimate visitor requests are shown in green.
- **Server Response**: The server's responses to the malicious SYN requests and subsequent connection timeout errors for legitimate requests can be observed.
- **Resource Exhaustion**: The high volume of SYN packets results in resource exhaustion, leading to server unresponsiveness.

#### 3. Identifying the Solution

**Tools for Analysis**:

- **Wireshark**: Use Wireshark to capture and analyze network traffic. Look for high volumes of SYN packets and incomplete TCP handshakes.
- **Log Analysis**: Review server logs to identify patterns and abnormal traffic spikes.
- **Network Monitoring**: Implement network monitoring tools to detect unusual traffic patterns in real-time.

**Preventive Measures**:

- **Rate Limiting**: Implement rate limiting to control the number of incoming SYN requests.
- **Firewall Rules**: Configure firewalls to filter and block suspicious SYN traffic.
- **Intrusion Detection Systems (IDS)**: Deploy IDS to detect and alert on potential SYN Flood attacks.
- **TCP Stack Tuning**: Adjust server TCP stack settings to handle incomplete connections more effectively.

## Files Used

- **Cybersecurity Incident Report.pdf**: Provides detailed analysis and documentation of the network attack.
- **How to Read a Wireshark TCP_HTTP.pdf**: Instructions for analyzing TCP and HTTP traffic using Wireshark.

## Conclusion

This repository serves as a resource for understanding and mitigating SYN Flood attacks. By analyzing network traffic and using various tools, you can gain insights into detecting and preventing such attacks, ensuring the stability and security of network services.
