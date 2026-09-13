# Common Network Security Threats

## 1. Introduction

Network security threats are malicious activities that target computer networks, systems, devices, or communication. These threats can affect the confidentiality, integrity, and availability of information and services.

This report discusses four common network security threats:

1. Denial-of-Service (DoS) and Distributed Denial-of-Service (DDoS)
2. Man-in-the-Middle (MITM)
3. IP Spoofing
4. DNS Poisoning/Spoofing

For each threat, this report explains how the attack works, provides a real-world example, describes its impact, and presents mitigation techniques.

---

# 2. DoS and DDoS Attacks

## 2.1 What is DoS/DDoS?

A Denial-of-Service (DoS) attack attempts to make a system, server, application, or network service unavailable to legitimate users.

A Distributed Denial-of-Service (DDoS) attack has the same general objective, but the malicious traffic comes from many systems or sources instead of a single source.

The main goal is to affect the availability of the targeted service.

## 2.2 How It Works

In a typical DoS attack, an attacker sends a large number of requests or packets to a target system. The target may become overloaded and unable to respond normally to legitimate users.

In a DDoS attack, the attacker uses multiple compromised or otherwise abused systems to generate traffic toward the target. Some DDoS attacks also use amplification, where a small request causes a much larger response to be sent toward the victim.

As the volume of unwanted traffic increases, network bandwidth, CPU, memory, or application resources may become exhausted.

## 2.3 Real-World Example

On February 28, 2018, GitHub experienced a major DDoS attack that temporarily made GitHub.com unavailable. GitHub reported that the attack used memcached servers that were accessible from the public Internet with UDP support enabled.

The attack used IP-address spoofing so that responses from memcached servers were directed toward GitHub. GitHub reported that the amplification factor could reach approximately 51,000 times the original request size.

The incident caused GitHub.com to be unavailable for several minutes before mitigation measures restored service.

## 2.4 Impact

A successful DoS/DDoS attack can cause:

* Website or application downtime
* Slow network performance
* Loss of availability for legitimate users
* Financial losses
* Damage to an organization's reputation
* Disruption of business operations

## 2.5 Mitigation

### 1. Traffic filtering and rate limiting

Firewalls, routers, and network security systems can filter unwanted traffic and limit excessive requests.

### 2. DDoS protection and traffic scrubbing

Organizations can use specialized DDoS protection services and upstream providers to detect malicious traffic and filter it before it reaches the target.

### 3. Prevent amplification and spoofing

Network administrators should disable unnecessary UDP services, secure publicly exposed services, and implement source-address validation and appropriate network filtering.

---

# 3. Man-in-the-Middle (MITM) Attack

## 3.1 What is MITM?

A Man-in-the-Middle attack occurs when an attacker positions themselves between two communicating parties and intercepts or modifies the communication.

For example:

```text
User  <---->  Attacker  <---->  Legitimate Server
```

The user and server may believe they are communicating directly with each other while the attacker is observing or manipulating the communication.

## 3.2 How It Works

A MITM attack generally requires the attacker to get into a position where network communication can be observed or redirected.

Common situations that can enable MITM attacks include:

* Untrusted public Wi-Fi
* Weak network authentication
* Rogue access points
* Compromised routers
* Weak or improperly implemented encryption
* Failure to properly validate digital certificates

The attacker may attempt to capture credentials, session information, or other sensitive information. In some cases, the attacker can also modify information while it is being transmitted.

## 3.3 Real-World Example

A well-known example involved Lenovo laptops that were shipped with Superfish VisualDiscovery software.

The software used a trusted root certificate and intercepted HTTPS connections so that it could inspect encrypted web traffic and display advertisements. The U.S. Federal Trade Commission described the software as acting as a man-in-the-middle between consumers' browsers and websites, including encrypted websites.

The design created serious security risks because the software weakened protections that normally help browsers verify secure connections.

## 3.4 Impact

A successful MITM attack can result in:

* Theft of login credentials
* Exposure of sensitive information
* Session hijacking
* Modification of data in transit
* Privacy violations
* Installation or delivery of malicious content

## 3.5 Mitigation

### 1. Use strong encryption

Use HTTPS/TLS, secure VPNs, and other properly configured encrypted communication protocols.

### 2. Validate certificates

Applications and browsers should properly validate server certificates and should not ignore certificate warnings without a legitimate reason.

### 3. Avoid untrusted networks

Avoid accessing sensitive services through unknown or untrusted Wi-Fi networks. Organizations should also use strong wireless authentication and network segmentation.

---

# 4. IP Spoofing

## 4.1 What is IP Spoofing?

IP spoofing is a technique in which an attacker changes the source IP address of network packets so that the packets appear to come from another system or address.

The spoofed address can make it more difficult to determine the actual source of traffic.

IP spoofing is often used as part of another attack rather than being the final objective itself.

## 4.2 How It Works

Normally, a packet contains a source IP address indicating where the packet supposedly originated.

In IP spoofing, an attacker creates packets containing a forged source IP address.

Conceptually:

```text
Actual Attacker
      |
      | Packet with forged source IP
      v
Target believes traffic came from another address
```

Because the source address is forged, the target may incorrectly associate the traffic with another system.

IP spoofing can be particularly useful in certain DDoS amplification attacks because responses can be directed toward a victim while hiding the attacker's actual source address.

## 4.3 Real-World Example

GitHub's February 2018 DDoS incident is also an example of IP spoofing being used as part of a larger attack.

According to GitHub's incident report, attackers abused publicly accessible memcached servers using UDP. Spoofed IP addresses were used so that memcached responses were sent toward GitHub instead of the attacker.

This allowed the attackers to generate a much larger amount of traffic toward GitHub than they sent themselves.

## 4.4 Impact

IP spoofing can be used to:

* Hide the actual source of network traffic
* Support DDoS attacks
* Enable reflection and amplification attacks
* Bypass poorly designed source-address controls
* Make network investigation more difficult

IP spoofing alone does not necessarily provide unauthorized access to a system. Its danger often comes from how it is combined with other attack techniques.

## 4.5 Mitigation

### 1. Source address validation

Network administrators should implement ingress and egress filtering to prevent packets with invalid or unexpected source addresses from entering or leaving a network.

### 2. Use network security controls

Firewalls, access-control lists (ACLs), and intrusion detection/prevention systems can help identify and filter suspicious traffic.

### 3. Secure network infrastructure

Organizations should follow routing and network-security best practices, including source-address validation and appropriate filtering at network boundaries.

---

# 5. DNS Poisoning/Spoofing

## 5.1 What is DNS Poisoning?

DNS poisoning, also called DNS cache poisoning, is an attack in which false DNS information is inserted into a DNS resolver's cache.

DNS normally translates domain names into IP addresses.

For example:

```text
example.com
      |
      v
DNS Server
      |
      v
Correct IP Address
```

During DNS poisoning, an attacker attempts to cause the DNS resolver to store a false result:

```text
example.com
      |
      v
DNS Server
      |
      v
Attacker-controlled IP Address
```

Users may then be directed to an incorrect or malicious destination.

## 5.2 How It Works

A DNS resolver sends queries to obtain information about a domain.

In a cache-poisoning attack, an attacker attempts to provide a forged DNS response that appears to be a legitimate response to the resolver's query.

If the forged response is accepted and cached, users relying on that resolver may receive incorrect DNS information until the poisoned record expires or is removed.

The historical Kaminsky DNS vulnerability demonstrated how weaknesses in the DNS protocol could be exploited to poison caching recursive resolvers with spoofed information.

## 5.3 Real-World Example

In 2008, security researcher Dan Kaminsky disclosed a serious DNS cache-poisoning weakness.

The Internet Systems Consortium (ISC) documented the issue as CVE-2008-1447. The weakness affected the DNS protocol and could allow attackers to poison caching recursive resolvers with spoofed data.

ISC stated that DNSSEC was the definitive solution and recommended that administrators running affected BIND versions apply the appropriate security updates.

## 5.4 Impact

DNS poisoning can cause:

* Users to be redirected to malicious websites
* Credential theft
* Phishing attacks
* Malware delivery
* Incorrect network routing
* Loss of trust in DNS services
* Service disruption

## 5.5 Mitigation

### 1. Deploy DNSSEC

DNSSEC provides mechanisms for validating the authenticity and integrity of DNS information and is an important defense against forged DNS responses.

### 2. Keep DNS software updated

DNS servers and resolvers should be regularly patched and maintained to address known vulnerabilities.

### 3. Use secure DNS configurations

Administrators should use secure resolver configurations, restrict unnecessary DNS access, monitor unusual DNS behavior, and use protections such as randomized query parameters and DNS cookies where appropriate.

---

# 6. Comparison of Network Security Threats

| Threat                 | Attack Vector                                      | Who is at Risk?                                   | Difficulty     | Ease of Mitigation |
| ---------------------- | -------------------------------------------------- | ------------------------------------------------- | -------------- | ------------------ |
| DoS/DDoS               | Excessive or malicious network/application traffic | Websites, servers, organizations, online services | Medium to High | Medium             |
| MITM                   | Intercepting or modifying communication            | Users, organizations, applications                | Medium to High | Medium             |
| IP Spoofing            | Forged source IP addresses in network packets      | Networks, servers, DDoS targets                   | Medium         | Medium             |
| DNS Poisoning/Spoofing | Forged or manipulated DNS information              | DNS users, organizations, websites                | High           | Medium             |

### Comparison Summary

DoS/DDoS primarily affects **availability**.

MITM primarily threatens **confidentiality and integrity** because attackers may observe or modify communication.

IP spoofing is often a supporting technique used to hide the source of traffic or enable reflection/amplification attacks.

DNS poisoning primarily threatens the **integrity and reliability of name resolution** and can redirect users to attacker-controlled destinations.

---

# 7. Conclusion

Network security threats can affect organizations in different ways. Some attacks focus on making services unavailable, while others attempt to steal information, manipulate communication, or redirect users to malicious destinations.

DoS/DDoS, MITM, IP spoofing, and DNS poisoning demonstrate why organizations need multiple layers of network security.

## Key Takeaways for Network Administrators

1. **Monitor and control network traffic:** Use firewalls, filtering, rate limiting, intrusion detection, and appropriate network segmentation to reduce exposure to malicious traffic.

2. **Protect communication and authentication:** Use properly configured encryption, certificate validation, secure authentication, and trusted network connections to reduce MITM risks.

3. **Secure network infrastructure and DNS:** Keep network and DNS software patched, implement source-address validation, use DNSSEC where appropriate, and disable unnecessary publicly accessible services.

A strong network-security strategy should combine preventive controls, continuous monitoring, regular updates, and an effective incident-response process.

---

# 8. References

1. **National Institute of Standards and Technology (NIST)** — Man-in-the-Middle Attack Glossary and NIST security guidance.

2. **National Institute of Standards and Technology (NIST SP 800-189)** — *Resilient Interdomain Traffic Exchange: BGP Security and DDoS Mitigation.*

3. **Cybersecurity and Infrastructure Security Agency (CISA)** — *UDP-Based Amplification Attacks.*

4. **GitHub Security** — *February 28th DDoS Incident Report*, documenting the 2018 GitHub memcached amplification attack.

5. **Federal Trade Commission (FTC)** — *Lessons from FTC's Lenovo Case: Pay Attention to the Man in the Middle.*

6. **Internet Systems Consortium (ISC)** — *CVE-2008-1447: DNS Cache Poisoning Issue ("Kaminsky bug").*

7. **Cisco Talos** — *DNS Hijacking Abuses Trust in Core Internet Service*, documenting the Sea Turtle DNS hijacking campaign.

