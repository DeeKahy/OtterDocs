## Tools

### Trace route

This diagnostic tool determines the path taken to a destination.  
`TRACERT example.com`

### DNS Checking

To figure out if and where your DNS record is and what it's pointing to, you can use  
[What's my DNS](https://www.whatsmydns.net/) and give it the domain you want to check.

## DNS Records Explained

| Record Type | Description                                          |
|-------------|------------------------------------------------------|
| A           | Maps a domain name to an IPv4 address                |
| AAAA        | Maps a domain name to an IPv6 address                |
| CNAME       | Creates an alias for a domain name                   |
| TXT         | Stores text-based information about a domain         |
| SRV         | Specifies the hostname and port number for a service |

## Overview

The Domain Name System (DNS) translates human-readable domain names (e.g. store.example.com) into IP addresses that
computers can understand. DNS entries store this information and allow users to access websites and other online
resources by typing in a domain name. Changes to DNS entries may take some time to propagate across the internet. There
are various types of DNS entries that can be created or modified in the DNS Zone Editor, such as A records (mapping
domain names to IPv4 addresses) and CNAME records (creating aliases for domain names). Understanding different types of
DNS entries can help manage a domain and ensure access to online resources.

### A Record

An A record, or Address record, is a type of DNS record that maps a domain name to an IPv4 address. A records are used
to point a domain name to a specific IP address, allowing users to access the corresponding website or resource by using
the domain name.

For example, if you have a website hosted at the IP address 192.0.2.1, you can create an A record for the domain
name www.example.com that points to that IP address. This will allow users to access your website by
typing www.example.com into their web browser, rather than having to remember the IP address.

A records are used for many different types of resources, including websites, email servers, and other types of servers.
They are a critical part of the DNS system, and they play a vital role in ensuring that domain names are properly mapped
to the correct IP addresses and resources.

### AAAA Record

An AAAA record, or Quad-A record, is a type of DNS record that maps a domain name to an IPv6 address. Like A records,
AAAA records are used to point a domain name to a specific IP address, allowing users to access the corresponding
website or resource by using the domain name.

The main difference between A records and AAAA records is that A records use IPv4 addresses, which are 32-bit numbers,
while AAAA records use IPv6 addresses, which are 128-bit numbers. IPv6 addresses are becoming increasingly important as
the internet continues to grow, and AAAA records are used to support the growing number of devices and services that use
IPv6.

If you have a website or other resource that is hosted on an IPv6 address, you can create an AAAA record for the domain
name that points to that address. This will allow users to access your website or resource using the domain name, rather
than having to remember the IPv6 address.

### CNAME

A CNAME record, or Canonical Name record, is a type of DNS record that creates an alias for a domain name. CNAME records
are used to point a domain name to another domain name, rather than to an IP address.

For example, if you have a website hosted at the domain name www.example.com, you can create a CNAME record for the
domain name mywebsite.com that points to www.example.com. This will allow users to access your website by typing
either www.example.com or mywebsite.com into their web browser.

CNAME records are useful when you want to use multiple domain names to access the same website or resource. For example,
you might want to use both www.example.com and example.com to access your website, or you might want to use different
domain names for different regions or languages.

In addition to pointing a domain name to another domain name, CNAME records can also be used to point a domain name to a
subdomain. For example, you might create a CNAME record for the domain name blog.example.com that points
to www.example.com, allowing users to access your blog by typing blog.example.com into their web browser.

CNAME records are a useful tool for managing multiple domain names and subdomains, and they are an important part of the
DNS system. By understanding how CNAME records work, you can better manage your domain and ensure that your website and
other online resources are easily accessible to your users.

### TXT Records

A TXT record, or Text record, is a type of DNS record that can be used to store text-based information about a domain.
TXT records are commonly used to store SPF records, which are used to prevent email spoofing, and to store information
about domain ownership and other types of information.

TXT records are stored in the DNS zone file, and they can be retrieved by DNS clients using a DNS query. The information
stored in a TXT record is typically a series of key-value pairs, separated by a delimiter.

TXT records are a flexible and useful tool for storing various types of information about a domain. They are often used
for security purposes, such as storing SPF records, and for storing other types of metadata about a domain.

### SRV record

SRV records (Service records) are DNS records that specify the hostname and port number for a particular service, such
as SIP or XMPP. They allow clients to locate servers that provide a specific service. SRV records consist of fields that
specify the service, protocol, name, and other information about the server, and they can also specify the priority and
weight of the server. They are stored in the DNS zone file and are used in conjunction with other DNS records, like A
and AAAA records, to route traffic to the correct server. SRV records are important for ensuring that clients can access
servers that provide specific services.

```r
_minecraft._tcp.example.otterhosting.net 86400 SRV 10 20 5060 node1.otterhosting.net.
```
#### In short
this example allows anybody to add `example.otterhosting.net` to their minecraft server list, and it will join the 
server that is at `node1.otterhosting.net:5060`

#### Explanation
This SRV record specifies the hostname `node1.otterhosting.net` and port number `5060` for the `_minecraft._tcp` service. 
The fields `10` and `20` represent the priority and weight of the server, respectively.

The `_minecraft._tcp` service is a custom service that is used to locate servers for the game Minecraft. This SRV record
allows clients to connect to a Minecraft server hosted at `node1.otterhosting.net` using the specified port number.

The `86400` value at the beginning of the record specifies the time-to-live (TTL) for the record, which is the length of
time that the record will be cached by DNS resolvers. This value is given in seconds.




