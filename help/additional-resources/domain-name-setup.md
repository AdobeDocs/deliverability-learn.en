---
title: Domain name setup
description:  Learn .
feature: Deliverability
kt: 
thumbnail: 
doc-type: article
activity: understand
team: ACS
---

# Domain name setup

This document describes the business and technical requirements for domain name setup and delegation. You will need to select an email sending subdomain and, optionally, an externally facing subdomain to host web components (landing pages, opt-out page) for the Adobe platform you are using.

## Sub-Domains

With Adobe, digital marketing can truly become the contextual engine that powers your brand’s customer engagement marketing program.  Email continues to be the foundation of digital marketing programs. However, reaching the inbox has become more difficult than ever.

Creating a sub-domain for email campaigns allows brands to isolate varying types of traffic (marketing vs. corporate for example) into specific IP pools and with specific domains, which will speed the [IP warming process](../../help/additional-resources/increase-reputation-with-ip-warming.md) and improve deliverability overall. If you share a domain and it gets blocked or added to the block list it could impact your corporate mail delivery, but reputation issues or blocks on a domain specific to your email marketing communications will impact just that flow of email.  Using your main domain as the sender or ‘From’ address for multiple mail streams could also break email authentication, causing your messages to be blocked or placed in the spam folder. 

### Delegation
Domain name delegation is a method that allows the owner of a domain name (technically: a DNS zone) to delegate a subdivision of it (technically: a DNS zone under it, which can be called a sub-zone) to another entity. Basically, if a customer is handling the zone "example.com", he can delegate the sub-zone "marketing.example.com" to Adobe Campaign.

This means that Adobe Campaign’s DNS servers will have full authority on only that zone and not the top-level domain. Adobe Campaign’s DNS servers will provide authoritative answers to queries on domain names in that zone, such as "t.marketing.example.com" itself but not “www.example.com”.

By delegating a sub-domain for use with Adobe Campaign, clients can rely on Adobe to maintain the DNS infrastructure required to meet industry-standard deliverability requirements for their email marketing sending domains, while continuing to maintain and control DNS for their internal email domains.  Sub-domain delegation allows:

Clients to keep their brand image by using a DNS alias with its domain names
Adobe to autonomously implement all the technical best practices to fully optimize deliverability during emailing

## DNS Setup Options

In order to provide a cloud-based managed service, Adobe strongly encourages clients to use sub-domain delegation when deploying Adobe Campaign.  However, Adobe does offer clients an alternative option – CNAME setup – for configuring DNS.

| Option | Description | Adobe Responsibilities | Client Responsibilities |
|--- |--- |--- |--- |
| Sub-domain delegation to Adobe Campaign | Client delegates a sub-domain (email.example.com) to Adobe. In this scenario, Adobe is able to deliver the Campaign as a managed service by controlling and maintaining all aspects of DNS that are required for delivering, rendering and tracking of email campaigns. | Complete management of the sub-domain and all DNS records required for Adobe Campaign. | Proper delegation of the sub-domain to Adobe |
|Use of CNAMEs | Client creates a sub-domain and uses CNAMEs to point to Adobe-specific records.  Using this setup, both Adobe and the customer share responsibility for maintaining DNS. | Management of DNS records required for Adobe Campaign. | Creation and control of the sub-domain and creation/management of the CNAME records required for Adobe Campaign. |

