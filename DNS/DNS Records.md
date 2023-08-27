## About DNS Lookup Tool

DNS stands for Domain Name System. The system is responsible for converting a hostname (dnschecker.org) to a computer-friendly IP address.

When an end-user enters a domain or URL in its browser search bar, DNS servers process the request and translate them into a respective IP address to help browsers load relevant results.

Consider DNS Lookup as a map or phone book to find your respective searches for a better understanding.

You all know that we need a proper address to reach a specific destination. Same with the internet world. All smart devices, phones, laptops, tablets, TVs, etc., communicate over the internet through a series of numbers called the [IP Address](https://dnschecker.org/whats-my-ip-address.php). DNS Servers eliminate the need for humans to memorize complex IP numeric addresses. The DNS resolution involves converting a human-friendly domain name into a computer-friendly IP address. [DNS servers](https://dnschecker.org/dns-servers.php) take all the responsibility for delivering relevant results to the user.

As discussed earlier, humans cannot learn long number strings (IP Address). Therefore, by simply typing the website's name (www.amazon.com), the DNS server provides the IP Address associated with that domain.

The DNS server can either be on ISP or your local network. The translated domain (into IP address) is accessed by other devices such as routers to channel your search results.

After knowing how DNS Lookup works, let us discuss its **two major types**...

-   **Forward DNS Lookup**
    
    Searching a domain name to find its IP Address is referred to as forwarding DNS Lookup. A typical type allows users to put the domain name to get respective IP addresses.
    
-   **Reverse DNS Lookup**
    
    Contrary to forwarding DNS Lookup, DNS reverse lookup identifies the domain name using the IP Address. Email servers use this lookup method to identify valid receivers.
    

## What is a DNS record?

The **DNS records** are the mapping files containing the instructions to provide the following information related to a domain.

-   IP (IPV4/IPv6) is associated with that domain.
-   How to handle the DNS requests for that domain.

The **DNS lookup tool** fetches all the DNS records for a domain and reports them in a priority list.

Use options to perform DNS lookup against [Google](https://dnschecker.org/dns/Global/google), [Cloudflare](https://dnschecker.org/dns/Global/cloudflare), [OpenDNS](https://dnschecker.org/dns/Global/opendns), or the domain's authoritative name server(s). Therefore, if you change your web hosting or DNS records, those changes should reflect instantly.

To check that you have configured the correct DNS records for your domain, use the [DNS lookup tool](https://dnschecker.org/all-dns-records-of-domain.php) to verify your DNS records to avoid downtime. The DNS records include A, AAAA, CNAME, MX, NS, PTR, SRV, SOA, TXT, CAA, DS, DNSKEY, etc.

Select **any record** for lookup or select **"ALL"** to get all common DNS records for a domain.

### Different Types of DNS Records

1.  **A record:** the most basic type of record, also known as address record, provides an IPv4 address to a domain name or sub-domain name. That record points the domain name to an IP address.
2.  **AAAA record:** maps the hostname to 128-bits IPv6 address. For a long time, 32-bits IPv4 addresses served the purpose of identifying a computer on the internet. But due to the shortage of IPv4, IPv6 was created. The four "A" s (AAAA) are mnemonic to represent that IPv6 is four times larger in size than IPv4.
3.  **CNAME record:** also known as **Canonical Name record**, creates an alias of one domain name. The aliased domain or sub-domain gets all the original Domain's DNS records and is commonly used to associate subdomains with existing main domain.
4.  **MX record:** also known as **Mail Exchange records**, tells which mail exchange servers are responsible for routing the email to the correct destination or mail server. For detailed analysis, use [MX Record Lookup](https://dnschecker.org/mx-lookup.php).
5.  **NS record:** also known as **Name Server records,** points to the name servers which have authority in managing and publishing DNS records of that domain. These are the DNS servers that are authoritative to handle any query related to that domain. Use [NS Lookup Tool](https://dnschecker.org/ns-lookup.php) to dig deeper.
6.  **PTR record:** also known as **Pointer record,** points the IPv4 or IPv6 address to its machine's hostname. It provides a [reverse DNS record](https://dnschecker.org/reverse-dns.php), also known as rDNS record, by pointing an IP address to the server's hostname.
7.  **SRV record:** also known as **Service record,** indicates which specific services the domain operates along with port numbers. Some Internet protocols such as the Extensible Messaging and Presence Protocol (XMPP) and the Session Initiation Protocol (SIP) often require SRV records.
8.  **SOA record:** also known as **Start of Authority records,** provides essential information about the domain like identifying master node of domain authoritative nameserver, an email of the domain administrator, the serial number of DNS zone, etc.
9.  **TXT record:** allows the website's administrator to insert any arbitrary text in the DNS record.
10.  **CAA record:** also known as **Certification Authority Authorization record**, reflects the public policy regarding the issuance of digital certificates for the domain. If no CAA record is present for your domain, any Certification Authority can issue an SSL certificate for your domain. However, by using this record, you can restrict which CA is authorized to issue digital credentials for your domain.
11.  **DS record:** also known as **Delegation Signer record,** and it consists of the unique characters of your public key and its related metadata like Key Tag, Algorithm, Digest Type and cryptographic hash value called Digest.
12.  **DNSKEY record:** also known as **DNS Key record,** containing public signing keys like **Zone Signing Key (ZSK)** and **Key Signing Key (KSK)**. The **DS** and **DNSKEY** records serve to validate the authenticity of DNS records returned by the DNS Server.