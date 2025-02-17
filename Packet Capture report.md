#  PCAP Traffic Analysis Report

## Overview
This report analyzes network traffic using **DynamiteLab**, the successor of PacketTotal. 

I`ve initiated this project in order to detect potential threats, abnormal activity, and patterns in the nbetwork traffic.

The following PCAP file was taken from the website **[Malware Traffic Analysis (July 19, 2019)](https://www.malware-traffic-analysis.net/2019/07/19/index.html)** and uploaded to [DynamiteLab](https://dynamitelab.com/) for investigation.

## Analysis Details
- **File Name:** 2019-07-19-traffic-analysis-exercise.pcap
- **Total IP Addresses:** 37
- **Total Events:** 211

Screenshot [here](https://ibb.co/QFVrDBys)

## Significant Findings

###  1. High Percentage of TCP Traffic (56.87%)
The majority of network traffic is TCP-based, (compared to UDP 43.13%). Screenshot [here](https://ibb.co/RTtB4xJ6)

This could be either normal traffic (with maybe large files transfers) or network congestion, where too much traffic is trying to pass through a limited bandwidth.

I would recommend consistent monitoring for abnormal TCP connections, especially suspicious data flows.

### 2. Services Used:
   - **DNS (34.60%)**
   - **HTTP (18.01%)**
   - **Unknown (15.17%)**
   - **SSL (10.90%)**
   - **Kerberos TCP (8.53%)**
     
In my opinion, the high percentage of ‘Unknown’ traffic requires further analysis of port and protocol, as it might indicate malware activity. Screenshot [here](https://ibb.co/yc3DvTPh)

### 3. High volume of DNS Traffic (port 53)
The DNS percentage traffic 34.65% could suggest (besides normal network activity) DNS tunneling, a method used by attackers to exfiltrate data or bypass security controls or misconfiguration. Screenshot [here](https://ibb.co/nNHKLWpb)

### 4. Unusual Connection Duration and Data Volume
We could notice certain connections lasting quite long (6624 seconds) and transferring large volumes of data (7.2MB sent, 8.2MB received). Screenshot [here](https://ibb.co/vCb7J1hr)

As a recommendation I suggest to further investigate, analyze and determine whether the activity is malicious or not.

## Further steps recommended for the investigation
- To determine the true nature of the "Unknown" traffic, we could make use of Wireshark.
- To perform endpoint analysis if it`s possible (to look for suspicious processes or registry entries)
- To correlate what I found (IP addresses, domain names etc)  with threat intelligence databases (e.g:VirusTotal)
- To analyze the content of the data being exchanged in the big transfer and to see if it was made within a legitimate activity

