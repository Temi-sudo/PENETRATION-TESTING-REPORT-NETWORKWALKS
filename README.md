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

## 1. Liability Disclaimer:
All reconnaissance queries and network scans in this report were conducted exclusively within lab environments owned by the author or with explicit permission for educational purposes on specified external domains.<br> 
The methodologies presented are for defensive research and ethical hacking training only. Unauthorized activities against third-party systems without consent are illegal and carry severe penalties. 
<br>The authors disclaim responsibility for any misuse of the information; each individual is accountable for their actions, which can lead to criminal charges and professional repercussions.
## 2. Project Overview:
This report details the footprinting of the <code>networkwalks.com</code> domain using Kali Linux and scanning of my local network using <b>Zenmap</b>, as part of my internship at <b>Networkwalks</b>. <br>
Two main modules are documented: Footprinting of <code>networkwalks.com</code> domain and active network discovery of my local network.<br>
The report includes command syntax, observed results, attacker significance, and screenshot evidence, demonstrating the process from open-source intelligence (OSINT) collection to active host mapping.
## 3. Tools Used:
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
  
  ## 4. Activities Performed and Findings:
  ### 4.1 Footprinting & Reconnaissance:
  I conducted reconnaissance on the networkwalks.com domain using six Kali Linux tools: <code>whois</code>, <code>whatweb</code>, <code>nslookup</code>, <code>curl -I</code>, <code>wafw00f</code>, and <code>dnsrecon</code>. Each tool served a distinct purpose and gathered different information about the target. <br>
  <pre><code>whois networkwalks.com</code></pre>
  <b>whois</b> provided domain registration details and name servers. 
  <pre><code>whatweb networkwalks.com</code></pre>
  <b>whatweb</b> identified technologies such as WordPress 7.0.4. used by the website
  <pre><code>nslookup networkwalks.com</code></pre>
  Nslookup resolved the domain name to IP address 192.232.216.135.
  <pre><code>curl -I https://networkwalks.com</code></pre>
  <b>curl -I</b> showcased HTTP response headers and revealed the WordPress REST API endpoint. 
  <pre><code>wafw00f networkwalks.com</code></pre>
  <b>wafw00f</b> confirmed ModSecurity as a Web Application Firewall. 
  <pre><code>dnsrecon -d networkwalks.com</code></pre>
  <b>dnsreco</b> enumerated DNS records, including name and mail servers.
  ### 4.2 Network Scanning with Zenmap
  For the second activity, network discovery was performed using Zenmap. <br>
  The initial step involved identifying my local IP address and subnet via the Windows <code>ipconfig</code> command. <br>
  Next, Zenmap's <b>Ping Scan</b> feature was employed to discover all active hosts on my network and gather their IP and MAC addresses,    leading to network topology generation.<br>
  The example results provided in the practical identified two live hosts:

10.0.0.1
10.0.0.4
10.0.0.19
10.0.0.5
The example results also included two MAC addresses.

  ## 5. Risk Analysis / Impact
  <table>
      <tr>	
        <th>#</th>
        <th>Technical Finding</th>
        <th>Evidence / Observation</th>
        <th>Potential Impact</th>   
          <th>Severity</th>     
      </tr>
      <tr>
        <td>1</td>
        <td><b>Web technology information exposed</b></td> 
        <td>WhatWeb identified WordPress <code>7.1.4</code> & WP Download Manager <code>3.3.77</code>; DNSRecon exposed <code>BIND 9.16.23-RH</code></td>
        <td>Attackers can exploit exposed technology and version information to discover software that requires security evaluation, allowing them to compare specific software versions to public CVE exploit databases.</td>  
      <td>🟠 Medium</td>   
      </tr>
      <tr>
        <td>2</td>
        <td><b>Server IP address identifiable</b></td> 			
        <td>Nslookup resolved the domain to 192.232.216.135</td>
        <td>Provides information about the network location of the web service</td>    
            <td>🟡 Low</td>   
      </tr>
        <tr>
        <td>3</td>
        <td><b>HTTP technical information exposed</b></td>
        <td>Curl returned HTTP response headers and exposed /wp-json/</td>
        <td>May assist technology fingerprinting and further enumeration</td>      
              <td>🟡 Low</td>   
      </tr>
        <tr>
        <td>4</td>
        <td><b>WAF technology identifiable</b></td> 			
        <td>Wafw00f identified ModSecurity (SpiderLabs)</td>
        <td>Reveals information about the web application’s security architecture</td>
              <td>🟡 Low</td>   
      </tr>
        <tr>
        <td>5</td>
        <td><b>DNS infrastructure information exposed</b></td> 			● Medium
        <td>DNSRecon identified DNS, mail and service-related records</td>
        <td>DNS information can help build a broader infrastructure profile</td>
              <td>🟠 Medium</td>   
      </tr>
        <tr>
      <td>6</td>
        <td><b>Multiple live hosts visible on local network</b></td> 	
        <td>Zenmap identified four live hosts in the example network Zenmap discovered 3 live nodes on 192.168.43.0/24 and open ports 135, 139, 445/tcp on 10.0.0.10</td>
        <td>Unknown or unauthorized devices may potentially be present on a network</td>
              <td>🟠 Medium</td>   
      </tr>
  </table>

  Risk Level Key: 🔴 Critical | 🟠 Medium | 🟡 Low<br>
  <p>The dangers listed above are observations based on footprinting and scanning efforts, not known vulnerabilities.</p>

<p>The practical activities focused mostly on information collection and host finding. There was no exploitation or vulnerability validation in these two modules.</p>

<p>Thus, the availability of information such as a software version, IP address, or DNS record does not imply that the system is susceptible. Additional authorized security testing would be necessary to confirm any potential vulnerability.</p>

 ## 6. Recommendations
Based on the observations, these security enhancements, which include establishing defensive mechanisms to limit both external and internal attack surfaces, are as follows:

1. <b>Examine publicly available information and disable Version Banners and Meta Generators</b><br>
A routine assessment of what information about the organization (web technologies, CMS, plugins, version banners, and meta generators) is publicly available and should be reduced to the bare minimum.

2. <b>Regularly update softwares</b><br>
CMS platform (WordPress core), themes, plugins, and other web technologies should be updated regularly.

3. <b>HTTP headers hardening</b><br>
 Configure and review the web server or reverse proxy to strip identifying banners and enforce security headers.

4. <b>DNS records safeguard</b><br>
Ensure DNS record hardening by locking down published DNS zone records and registrar delegation against spoofing and dangling-record takeovers. Enable DNSSEC, Publish CAA records, Enforce email authentication (SPF, DKIM, DMARC)

5. <b>Enable and Tune ModSecurity web application firewall (WAF)</b><br>
Ensure <b>ModSecurity</b> web application firewall (WAF) engine (v2 or v3 <code>libmodsecurity</code>) is paired with the <b>OWASP Core Rule Set (CRS)</b>, tuning rules to prevent false positives, and enforcing strict request/response limits

6. <b>Carry out periodical internal network discovery</b><br>
Conduct scheduled audits across the internal network to verify active devices and detect unauthorized devices.

7. <b>Restrict local Windows SMB (Server Message Block) and NetBIOS services</b><br>
Limit or block how a Windows computer shares files, printers, network names, and remote services over the internal network.

8. <b>Maintain Accurate Network Topology Documentations</b><br>
 Ensure all network diagrams and records remain current, accurate, and accessible to support rapid troubleshooting, security audits, and infrastructure planning.

9. <b>Ensure Penetration Testing (pen test) Authorization</b><br>
Ensure written, pre-approved guidelines and boundaries authorizing a security test and defining how it runs to protect both the client and the pen tester team from outages, misunderstandings, and legal exposure.

 ## 7. Conclusion
In Week 2 of my Cybersecurity & Ethical Hacking internship, I carried out hands-on activities focused on footprinting, reconnaissance, and network scanning.<br>
In the Phase 1 footprinting activity, I used six Kali Linux tools (<code>whois, whatweb, nslookup, curl -I, wafw00f, and dnsrecon</code>)  to collect information about the target domain.<br>

<code>whois</code> provided the domain information, <code>whatweb</code> identified the web technologies, <code>nslookup</code> resolved domain names into IP addresses, <code>curl -I</code> inspected HTTP headers, <code>wafw00f</code>identified a ModSecurity WAF, and <code>dnsrecon</code> provided additional DNS information.<br>

During the Phase 2 Zenmap network scanning activity, I determined my local network configuration and identified active hosts using Windows <code>ipconfig /all</code> and Zenmap. I gathered IP and MAC address details and developed a network topology.<br>

The exercises demonstrated that gathering information is a fundamental component of cybersecurity.<br>

I learned that reconnaissance and scanning must consistently be conducted within an authorized scope.<br>

Finally, a high-quality cybersecurity report should describe what was performed, what was discovered, the significance of the observation, the risk it may create, and the measures that can be taken to mitigate that risk.<br>

## 8. Empirical Evidence Collected



