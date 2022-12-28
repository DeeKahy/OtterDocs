# Help full commands & links

## Trace route

This diagnostic tool determines the path taken to a destination.
`TRACERT example.com`

## DNS Checking

To figure out if and where your DNS record is and what it's pointing to, you can use
[What's my DNS](https://www.whatsmydns.net/) and give it the domain you want to check.

# DNS Records Explained

| Records | What they do |
|---------|--------------|
| A | An A record (Address Record) points a domain or subdomain to an IP address. |
| AAAA  | The AAAA record is similar to the A record, allowing you to point the domain to an Ipv6 address. |
| CNAME | A CNAME (Canonical Name) points one domain or subdomain to another domain name. |
| MX Entry | An MX Entry (Mail Exchanger) directs email to a particular mail server. Like a CNAME, MX Entries must point to a domain and never point directly to an IP address. |
| TXT | A TXT (Text) record was originally intended for human-readable text. These records are dynamic and can be used for several purposes |
| SRV  | An SRV (Service) record points one domain to another domain name using a specific destination port |

## Overview

DNS (Domain Name System) entries take a human-friendly name, such as store.example.com, and translate it to an IP address. The DNS can quickly be updated with some **propagation time**, which is the **length of time** needed to **update records** across the Internet. There are some DNS Entries you can create. The following DNS Entries can be created or modified from within the DNS Zone Editor.

## A Record

An A record (Address Record) points a domain or subdomain to an IP address. For example, you can use it for store.website.com or blog.website.com and point it to where you have your store. This is a common practice for people who use Amazon, eBay, Tumblr, etc.

For example, an A Record is used to point a logical domain name, such as "google.com," to the IP address of Google's hosting server, "74.125.224.147".

These records point traffic from example.com (indicated by @) and ftp.example.com to the IP address 66.147.224.236. They also point localhost.example.com to the server that the domain is hosted on. This allows the end-user to type in a human-readable domain while the computer can continue to work with numbers.

## AAAA Record

The AAAA record is similar to the A record, allowing you to point the domain to an Ipv6 address.

## CNAME

A CNAME (Canonical Name) points one domain or subdomain to another domain name, allowing you to update one A Record each time you make a change, regardless of how many Host Records need to resolve to that IP address.

These records point to www.example.com to example.com, imap.example.com to mail.example.com, and docs.example.com to ghs.google.com. The first record allows the domain to resolve to the same server with or without the WWW subdomain. The second record allows you to use an alternative subdomain for email hosting and delivery. The third record allows you to use the docs.example.com subdomain with G Suite, where you can use Google's document management system. This type of record requires additional configuration with Google.

## MX Entry

An MX Entry (Mail Exchanger) directs email to a particular mail server. Like a CNAME, MX Entries must point to a domain and never point directly to an IP address. See [E-Mail](E-Mail.md) for more information

## TXT Records

A TXT (Text) record was originally intended for human-readable text. These records are dynamic and can be used for several purposes. TXT records are commonly used for Google Verification.

The TXT Value is what the record 'points to,' but these records aren't used to direct any traffic. Instead, they're used to provide needed information to outside sources.

The First record is used for an SPF, Sender Policy Framework, records. Those records are used by many email systems to help identify if the email is coming from a trusted source, helping filter out spam or messages pretending to be from your domain (called spoofing).

The second record is used for DomainKeys, which is also used to verify that the email came from a trusted source.

## SRV record

An SRV (Service) record points one domain to another domain name using a specific destination port. In addition, SRV records allow specific services, such as VOIP or IM, to be directed to a separate location.