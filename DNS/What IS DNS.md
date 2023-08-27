## What is DNS propagation?

DNS propagation is the time DNS changes take to be updated across the internet on the globe. It can take up to 72 hours to propagate worldwide. You can check your DNS propagation results from [here.](https://dnschecker.org/)

## What is DNS resolution?

DNS resolution translates the domain name into the site's IP address. You need a site's IP address to know where it's on the internet. A website could have IPv4 or IPv6 addresses or both. Where the IPv4 address comes in the form of an A record and the IPv6 address comes in an AAAA record.

## How do DNS records propagate?

When you update your DNS records, it may take up to 72 hours for the changes to take effect. During this period, the ISPs worldwide update their DNS cache with new DNS information for your domain.

However, due to different DNS cache level, after DNS records changes, some of the visitors might be redirected to the old DNS server, for some time, and other can see the website from new DNS server, shortly after the changes. You can perform the A, AAAA, CNAME, and additional [DNS records lookup.](https://dnschecker.org/all-dns-records-of-domain.php)

## Why DNS propagation takes time?

Suppose you changed your domain's nameservers, and you requested to open your domain on the web browser. Your request will not go to the hosting directly.

Each of the ISP nodes first checks its DNS cache, whether it has the DNS information for that domain. If it is not there, it will look it up to save it for future use to speed up the DNA lookup process.

Thus, the new nameservers will not propagate instantly - ISPs have different cache refreshing levels, so some will still have the old DNS information in their cache.

But if after that time interval, still, your new DNS changes are not reflecting, then you go for a [DNS health check](https://dnschecker.org/domain-health-checker.php) to ensure that your DNS changes are up to the mark and are following the standards.

## How does the DNS process work?

Suppose you request to open the URL https://abc.com in your web browser's bar.

1.  The web browser first checks in its local cache whether it has the requested domain's IP address. If it's not present, then it will send the request to the Name Resolving Server.
2.  The Name Resolving Server checks its cache against that request. If it fails to find the requested domain's IP address, it will send that request to the Root Server.
3.  The Root Server only contains the server's IP address with TLD (Top Level Domain) related information. It will redirect the Name Resolving Server to the TLD server containing .com information.
4.  The TLD server provides the server's IP address (authoritative servers for requested URL https://abc.com) to the Name Resolving Server.
5.  The Name Resolving Server caches that information for a specific period (TTL) and passes that information to the requested's computer.
6.  The client's computer builds the connection with the authoritative server (containing the requested URL https://abc.com) for the requested content and caches the IP address's information in its browser for further use.

## Why is DNS not propagating?

The ISPs across the world have a different caching level. The DNS client or the server may cache the information the DNS records in its DNS cache. That information is temporarily cached, and DNS servers will go for the updated DNS information when TTL (Time to Live) expires.

## What will happen if the domain name does not exist?

The DNS server will return a name error, also known as an NXDomain response (for non-existent domain), to symbolize that the query's domain name does not exist.

## What is the port used by DNS?

DNS uses both TCP and UDP port 53. However, the most frequently used port for DNS is UDP 53. That is used when the client's computer communicates with the DNS server for resolving the specific domain name. Be sure, when using the UDP 53 for DNS, the maximum size of the query packet is 512 bytes.

TCP 53 is used primarily for Zone Transfers and when the query packet exceeds 512 bytes. That is true when [DNSSEC](https://dnschecker.org/dns-articles/dnssec-domain-name-system-security-extensions.html) is used, which adds extra overhead to the DNS query packet.

## What is DNS failure?

DNS failure means that the DNS server cannot convert the domain name into an IP address in a TCP/IP network. That failure may occur within the company's private network or the internet.

## Which are the best DNS servers?

Some of the best public DNS servers are

1.  **Google Public DNS:**
    -   **IPv4:**
        -   Primary: `8.8.8.8`
        -   Secondary: `8.8.4.4`
    -   **IPv6:**
        -   Primary: `2001:4860:4860::8888`
        -   Secondary: `2001:4860:4860::8844`
2.  **OpenDNS:**
    -   **IPv4:**
        -   Primary: `208.67.222.222`
        -   Secondary: `208.67.220.220`
    -   **IPv6:**
        -   Primary: `2620:119:35::35`
        -   Secondary: `2620:119:53::53`
3.  **Quad9 (Malware Blocking Enabled):**
    -   **IPv4:**
        -   Primary: `9.9.9.9`
        -   Secondary: `149.112.112.112`
    -   **IPv6:**
        -   Primary: `2620:fe::fe`
        -   Secondary: `2620:fe::9`
4.  **DNS.Watch:**
    -   **IPv4:**
        -   Primary: `84.200.69.80`
        -   Secondary: `84.200.70.40`
    -   **IPv6:**
        -   Primary: `2001:1608:10:25::1c04:b12f`
        -   Secondary: `2001:1608:10:25::9249:d69b`
5.  **Comodo Secure DNS:**
    -   **IPv4:**
        -   Primary: `8.26.56.26`
        -   Secondary: `8.20.247.20`
6.  **Cloudflare:**
    -   **IPv4:**
        -   Primary: `1.1.1.1`
        -   Secondary: `1.0.0.1`
    -   **IPv6:**
        -   Primary: `2606:4700:4700::1111`
        -   Secondary: `2606:4700:4700::1001`