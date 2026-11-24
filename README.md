# PENETRATION-TESTING-REPORT-NETWORKWALKS

# 🧩 OFFENSIVE SECURITY ASSESSMENT REPORT
## Footprinting &amp; Network Scanning
<table>
      <tr>
        <th>Field</th>
        <th>Description</th>
      </tr>
      <tr>
        <td><b>Pentester Name (Cybersecurity Expert)</b></td>
        <td><b>Temitope Adekunle Ogunji</b></td>
      </tr>
      <tr>
        <td><b>Program / Cohort	</b></td>
        <td>B084 — Networkwalks Cybersecurity & Ethical Hacking</td>
      </tr>
        <tr>
        <td><b>Date	</b></td>
        <td>13 November 2026</td>
      </tr>
        <tr>
        <td><b>Modules</b></td>
        <td><b>• Module:</b> W2-PM1: Multiple Kali Linux Tool <br>
            <b>• Module:</b> W2-PM5: Zenmap Local Subnet Scanning</td>
      </tr>
        <tr>
        <td><b>Authorized Target</b></td>
        <td>1. networkwalks.com & scanme.nmap.org (Authorized External Targets)
            2. My Local Network</td>
      </tr>
        <tr>
      <td><b>Authorized ?</b></td>
        <td>Yes (Written)</td>
      </tr>
        <tr>
        <td><b>Phases covered</b></td>
        <td><b>Phase 1:</b> Reconnaissance & Footprinting<br>
            <b>Phase 2:</b>Scanning & Network Discovery<br>
            <b>Phase 3:</b> In Progress</td>
      </tr>
        <tr>
      <td><b>Pentester Name (Cybersecurity Expert)</b></td>
        <td>Analyst</td>
      </tr>
  </table>

## Liability Disclaimer:
All reconnaissance queries and network scans in this report were conducted exclusively within lab environments owned by the author or with explicit permission for educational purposes on specified external domains.<br> 
The methodologies presented are for defensive research and ethical hacking training only. Unauthorized activities against third-party systems without consent are illegal and carry severe penalties. 
<br>The authors disclaim responsibility for any misuse of the information; each individual is accountable for their actions, which can lead to criminal charges and professional repercussions.
## Project Overview:
This report details the footprinting of the <code>networkwalks.com</code> domain using Kali Linux and scanning of my local network using <b>Zenmap</b>, as part of my internship at <b>Networkwalks</b>. <br>
Two main modules are documented: Footprinting of <code>networkwalks.com</code> domain and active network discovery of my local network.<br>
The report includes command syntax, observed results, attacker significance, and screenshot evidence, demonstrating the process from open-source intelligence (OSINT) collection to active host mapping.
## Tools Used:
<table>
      <tr>
        <th>Tools</th>
        <th>Usage</th>
      </tr>
      <tr>
        <td>Kali Linux & Windows</td>
        <td>Operating systems used for reconnaissance activities</td>
      </tr>
      <tr>
        <td><code>whois</code></td>
        <td>Find domain registration details (owner, dates, name servers).</td>
      </tr>
        <tr>
        <td><code>whatweb</code></td>
        <td>Fingerprint web technologies (server, CMS, plugins, IP).</td>
      </tr>
        <tr>
        <td><code>nslookup</code></td>
        <td>Resolve the domain name to its IP address using DNS.</td>
      </tr>
        <tr>
        <td><code>curl -I</code></td>
        <td>Read the website's HTTP response headers.</td>
      </tr>
        <tr>
    <td><code>wafw00f</code></td>
        <td>Detect whether a Web Application Firewall protects the site.</td>
      </tr>
        <tr>
       <td><code>dnsrecon</code></td>
        <td>Enumerate all DNS records (NS, MX, SPF, TXT, SRV).</td>
      </tr>
        <tr>
     <td><b>Zenmap (Nmap GUI)</b></td>
        <td>Scan the local subnet to find live hosts, IPs, and MAC addresses.</td>
      </tr>
        <tr>
     <td><b>Windows CMD</b></td>
        <td>Local IP and MAC address identification</td>
      </tr>
  </table>
  
  ## Activities Performed and Findings:
  ### Footprinting & Reconnaissance:
  I conducted reconnaissance on the networkwalks.com domain using six Kali Linux tools: whois, whatWeb, nslookup, curl -l, wafw00f, and DNSRecon. 
