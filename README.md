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
        <td>27th November 2026</td>
      </tr>
        <tr>
        <td><b>Modules</b></td>
        <td><b>• Module:</b> W2-PM1: Multiple Kali Linux Tool <br>
            <b>• Module:</b> W2-PM5: Zenmap Local Subnet Scanning</td>
      </tr>
        <tr>
        <td><b>Authorized Target</b></td>
        <td>1. networkwalks.com & scanme.nmap.org (Authorized External Targets)<br>
            2. My Local Network</td>
      </tr>
        <tr>
      <td><b>Authorized ?</b></td>
        <td>Yes (Written)</td>
      </tr>
        <tr>
        <td><b>Phases covered</b></td>
        <td><b>Phase 1:</b> Reconnaissance & Footprinting<br><br>
            <b>Phase 2:</b> Scanning & Network Discovery<br><br>
            <b>Phase 3:</b> Risk Analysis & Report Writing<br>
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
  <b>whois</b> provided domain registration details such as Registrar WHOIS Server: <code>whois.godaddy.com</code>, Registrar IANA ID: <code>146</code> and Name Servers:<code>NS6135.HOSTGATOR.COM and NS6136.HOSTGATOR.COM</code>  
  <pre><code>whatweb networkwalks.com</code></pre>
  <b>whatweb</b> identified information about target's server <b>IP</b><code>[192.232.216.135]</code> and <b>Country</b><code>[UNIED STATES]</code><br>
  Further observation reveals <b>MetaGenerator</b> technologies such as<code>[WordPress 7.1.5.WordPress Download Manager 3.3.80]</code> used by the website
  <pre><code>nslookup networkwalks.com</code></pre>
  <b>nslookup</b> cmd used Google DNS server<code>(8.8.8.8)</code> to resolve the domain name <code>networkwalks.com</code> to IP address <code>192.232.216.135.</code>
  <pre><code>curl -I https://networkwalks.com</code></pre>
  <b>curl -I</b> showed HTTP response headers and revealed the WordPress REST API endpoint at <code>https&#8203;://networkwalks.com/wp-json - https&#8203;://networkwalks.com/wp-json/wp/v2/pages/53)</code>. 
  <pre><code>wafw00f networkwalks.com</code></pre>
 <b>wafw00f</b> confirmed ModSecurity(SpiderLabs) as the Web Application Firewall. 
  <pre><code>dnsrecon -d networkwalks.com</code></pre>
 <b>dnsrecon</b> enumerated DNS records such as Start of Authority (SOA) record, NS (Name Server) record, MX (Mail Exchange) record, A (Address) record, TXT (text) record, and SRV (Service) record.
  ### 4.2 Network Scanning with Zenmap
  For the second activity, I performed network discovery using Zenmap. <br>
  The initial step involved identifying my local IP address and subnet via the Windows <code>ipconfig /all</code> command. <br>
  <p>Next, Zenmap's <b>Ping Scan</b> feature was employed to discover all active hosts on my network and gather their IP and MAC addresses, leading to network topology generation.</p>
<p>The example results provided in the practical identified two live hosts:</p>
<b>My Local Network IP</b> <code>192.168.43.24 - DESKTOP-2VTOGFN</code> <br>
PORT & STATUS<br>
<code>135/tcp  open  msrpc</code><br>
<code>139/tcp  open  netbios-ssn</code><br>
<code>445/tcp  open  microsoft-ds</code><br><br>

<b>Wi-Fi host IP</b> <code>192.168.43.1</code><br> 
PORT & STATUS<br>
<code>53/tcp  open  domain</code>
<p>The example results also included two MAC addresses</p>

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
        <td>WhatWeb identified WordPress <code>7.1.5</code> & WP Download Manager <code>.3.80</code>;<br> DNSRecon exposed <code>BIND 9.16.50-RH</code></td>
        <td>Attackers can exploit exposed technology and version information to discover software <br>that requires security evaluation, allowing them to compare specific software versions <br>to public CVE exploit databases.</td>  
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
        <td><b>DNS infrastructure information exposed</b></td> 
        <td>DNSRecon identified DNS, mail, and service-related records</td>
        <td>DNS information can help build a broader infrastructure profile</td>
              <td>🟠 Medium</td>   
      </tr>
        <tr>
      <td>6</td>
        <td><b>Multiple live hosts visible on local network</b></td> 	
        <td>Zenmap identified four live hosts in the example network, <br>discovered 3 live nodes on 192.168.43.0/24 and open ports 135, 139, 445/tcp</td>
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
Screenshot evidence collected<br>
### 8.1 Penetration Testing Evidence
<code>1. whois</code> result<br>
<img width="884" height="594" alt="whois" src="https://github.com/user-attachments/assets/fb20025e-25e6-49be-a62b-8454ce377016" />
<code>2. whatweb</code> result<br>
<img width="893" height="583" alt="whatweb" src="https://github.com/user-attachments/assets/9978f1a6-fe54-4f16-9232-ecc357f7e326" />
<code>3. nslookup</code> result<br>
<img width="897" height="588" alt="nslookup" src="https://github.com/user-attachments/assets/3bb2f07d-6771-4da4-a54a-6c63dc873c9b" />
<code>4. curl -I</code> result<br>
<img width="889" height="587" alt="curl -I" src="https://github.com/user-attachments/assets/11674dd9-21a9-4567-9480-e875cdd9029c" />
<code>5. wafw00f</code> result<br>
<img width="891" height="588" alt="wafw00f" src="https://github.com/user-attachments/assets/8cb14789-5314-4181-804e-a04d1e66cfe1" />
<code>6. dnsrecon</code> result<br>
<img width="889" height="597" alt="dnsrecon" src="https://github.com/user-attachments/assets/d374ea38-3397-4015-a120-ba3b0a5eb104" />

### 8.2 Network Scanning Evidence
<code>7. ipconfig /all</code> my local network result<br>
<img width="982" height="524" alt="ipconfig all - my local network" src="https://github.com/user-attachments/assets/cdc7b4ec-2999-47d6-9dff-35ec0979c3ce" />
<code>8. Host Zenmap Regular Scan</code> result<br>
<img width="944" height="654" alt="Host Zenmap Regular Scan" src="https://github.com/user-attachments/assets/f06a649c-f975-4197-b227-f84304a710e7" />
<code>9. Host Zenmap Regular Scan Topology</code> result<br>
<img width="1273" height="648" alt="Host Zenmap Scan Topology" src="https://github.com/user-attachments/assets/ae2f3b2c-e66a-4a4f-b739-9778a578bf54" />

