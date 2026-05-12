---
title: Domain name setup
description: Learn how to delegate a subdomain to Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4d52d197-d20e-450c-bfcf-e4541c474be4
TQID: https://experienceleague.adobe.com/ZSfcx8FGb6eAHVK-PVAjd1354b55o5n3oRfWg4A5vrg
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
    internal-label: Marketo Engage
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: b0bb9048-d951-48d8-8232-45cf248a7e27
    internal-label: Forms
  - id: b3b8a63f-51fc-40f6-a7d2-a31c5d49fb45
    internal-label: Configuration
  - id: e2290edd-b061-4880-9d79-dee306cf5aa9
    internal-label: Implementation
  - id: e64968b2-4ee5-47f9-8cae-0588f184b9eb
    internal-label: Programs
  - id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
    internal-label: Reporting
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
    internal-label: Resources
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5520579-b31f-4df7-9281-f0d9f91e2edc
    internal-label: Customer engagement
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: beb7a3c1-66ab-4786-b879-7621375b3c40
    internal-label: Email marketing
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
---
# Domain name setup

This document describes the business and technical requirements for domain name setup and delegation. You will need to select an email sending subdomain and, optionally, an externally facing subdomain to host web components (landing pages, opt-out page) for the Adobe platform you are using.

>[!NOTE]
>
>You can also set up new subdomains using the Control Panel (available as beta). Learn more in [this section](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html#must-read).

## Subdomains

With Adobe, digital marketing can truly become the contextual engine that powers your brand’s customer engagement marketing program.  Email remains the foundation of digital marketing programs. However, reaching the inbox has become more difficult than ever.

Creating a subdomain for email campaigns allows brands to isolate varying types of traffic (marketing vs. corporate for example) into specific IP pools and with specific domains, which will speed the [IP warming process](../../help/additional-resources/increase-reputation-with-ip-warming.md) and improve deliverability overall. If you share a domain and it gets blocked or added to the block list, it could impact your corporate mail delivery. However, reputation issues or blocks on a domain specific to your email marketing communications will impact just that flow of email.  Using your main domain as the sender or ‘From’ address for multiple mail streams could also break email authentication, causing your messages to be blocked or placed in the spam folder.

### Delegation

Domain name delegation is a method that allows the owner of a domain name (technically: a DNS zone) to delegate a subdivision of it (technically: a DNS zone under it, which can be called a sub-zone) to another entity. Basically, if a customer is handling the zone "example.com", he can delegate the sub-zone "marketing.example.com" to Adobe Campaign.

This means that Adobe Campaign’s DNS servers will have full authority on only that zone and not the top-level domain. Adobe Campaign’s DNS servers will provide authoritative answers to queries on domain names in that zone, such as "t.marketing.example.com" itself but not “www.example.com”.

By delegating a subdomain for use with Adobe Campaign, clients can rely on Adobe to maintain the DNS infrastructure required to meet industry-standard deliverability requirements for their email marketing sending domains, while continuing to maintain and control DNS for their internal email domains.  Subdomain delegation allows:

Clients to keep their brand image by using a DNS alias with its domain names
Adobe to autonomously implement all the technical best practices to fully optimize deliverability during emailing

## DNS setup options

In order to provide a cloud-based managed service, Adobe strongly encourages clients to use subdomain delegation when deploying Adobe Campaign.  However, Adobe does offer clients an alternative option – CNAME setup – for configuring DNS.

| Option | Description | Adobe Responsibilities | Client Responsibilities |
|--- |------- |--- |--- |
| Subdomain delegation to Adobe Campaign | Client delegates a subdomain (email.example.com) to Adobe. In this scenario, Adobe is able to deliver the Campaign as a managed service by controlling and maintaining all aspects of DNS that are required for delivering, rendering, and tracking of email campaigns. | Complete management of the subdomain and all DNS records required for Adobe Campaign. | Proper delegation of the subdomain to Adobe |
|Use of CNAMEs | Client creates a subdomain and uses CNAMEs to point to Adobe-specific records.  Using this setup, both Adobe and the customer share responsibility for maintaining DNS. | Management of DNS records required for Adobe Campaign. | Creation and control of the subdomain and creation/management of the CNAME records required for Adobe Campaign. |

## Required DNS records

| Record Type | Purpose | Examples Record/Content |
|--- |--- |--- |
| MX | Specify mail servers for incoming messages | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Sender Policy Framework | <i>email.example.com</i></br>"v=spf1 redirect=__spf.campaign.adobe.com" |
| DKIM (TXT) | DomainKeys Identified Mail | <i>client._domainkey.email.example.com</i></br>"v=DKIM1; k=rsa;" "DKIMPUBLICKEY HERE" |
| Hosts Records (A) | Mirror pages, image hosting, and tracking links, all sending domains | m.email.example.com IN A 123.111.100.99</br>t.email.example.com IN A 123.111.100.98</br>email.example.com IN A 123.111.100.97 |
| Reverse DNS (PTR) | Maps the client IP addresses to a client branded hostname | 18.101.100.192.in-addr.arpa domain name pointer r18.email.example.com |
| CNAME | Provides an alias to another domain name | t1.email.example.com is an alias for t1.email.example.campaign.adobe.com |


Domain-based Message Authentication, Reporting, and Conformance (DMARC) is recommended to authenticate mail senders and ensure that destination email systems trust messages sent from your domain.

Example of DMARC TXT record:

```
_dmarc.email.example.com

“v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com” 
```

You can implement DMARC manually or contact Adobe to assist you to set up DMARC for your brand. 

## Setup Requirements

### Sub-Domain delegation

This requires the client to create a subdomain in their DNS servers and define the name servers for this subdomain to be those maintained by Adobe.  For example, a client whose main domain name is “example.com” and who wants to delegate the management of “marketing.example.com” to Adobe for its email deliveries will have to materialize this delegation to add the following type records to its DNS:

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

Delegation of a domain name implies that this domain will be dedicated to delivering email via the Adobe Campaign platform, and therefore cannot be used for other means (for example, sending email from another email infrastructure).

During the setup process, Adobe will ensure the domain is attached to the Adobe incoming email infrastructure in order to manage and process the rebound emails coming back to these domains (MX type DNS record configuration).

### Use of CNAMEs

If the client chooses to use CNAMEs rather than delegate a subdomain to Adobe, during the setup phase, Adobe will provide the records to be placed in the client DNS servers and will configure the corresponding values in Adobe Campaign DNS servers.

## General requirements for Deployment

When implementing a new enterprise marketing solution, there are requirements for externally facing components.  These include hosting landing pages and web forms, setting up links and web pages to be tracked, displaying mirror pages, and configuring an opt-out page.

While these requirements are being managed through components hosted by both Adobe and the customer, they include URLs which can be seen by the recipients of the emails.  To avoid having URLs which indicate the underlying technical solution or hosting provider, subdomains can be set up to make this transparent to the recipients of the emails.  For example, when looking at a URL such as, http://www.customer.com/, the domain would be “www.customer.com”.  The subdomain of this would be “www”.

### Sub-Domain requirements

Determine the subdomain(s) to be used for branded URLs (mirror pages and tracking URLs) from the Adobe Campaign application.  Also decide what the “From Address”, “From Name” and “Reply-To Address” will be for each subdomain on email deliveries.

Complete the table below, first line is only an example.

| Subdomain | From address | From name | Reply-to address |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Customer | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* The purpose of the “Reply-To Address” field is when you want the recipient to reply to a different address than the “From Address”.  While not a required field, Adobe strongly recommends that the “Reply-To Address” be valid and linked to a monitored mailbox.  This mailbox must be hosted by the customer.  It could be a support mailbox, for example,  customercare@customer.com, where emails are read and responded to.
>* If no “Reply-To Address” is chosen by the customer, then the default address is always `<tenant>-<type>-<env>@<subdomain>`.
>* When the “Reply-To Address” is set up this way, replies will be sent to an unmonitored mailbox.
>* When sending emails from Adobe Campaign, the “From Address” mailbox is not monitored and marketing users cannot access this mailbox. Adobe Campaign also does not offer the ability to Auto-Reply or Auto-Forward emails received in this mailbox.
>* The Campaign From/Sender address and Error address cannot be “abuse” or “postmaster”.

## Delegating subdomains

The subdomain(s) chosen to be used for the Adobe Campaign platform must be delegated by creating four name server (NS) records.  This allows the subdomain to be properly delegated to Adobe.  Below is an example of a subdomain delegation and the respective DNS instructions.  Please substitute ‘emails.customer.com’ with the subdomain you wish to delegate.  Please note that the subdomain must be unique and cannot already be in use by another party (for example, an existing ESP or MSP).

| Delegated subdomain | DNS instructions |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com. </br> `<subdomain>` NS b.ns.campaign.adobe.com. </br> `<subdomain>` NS c.ns.campaign.adobe.com. </br> `<subdomain>` NS d.ns.campaign.adobe.com. |

## Tracking, Mirror pages, Resources

Once the email sending subdomain(s) is/are properly delegated to Adobe Campaign, the Adobe TechOps team will create two or more lower-level domains to manage tracking and mirror pages independently.

| Type | Domain |
|--- |--- |
| Mirror pages | m.`<subdomain>` |
| Tracking | t.`<subdomain>` |
| Resources | res.`<subdomain>` |

## Cloud deployment (optional)

This only applies if the Adobe Campaign Classic is fully hosted in the cloud by Adobe.  This is an optional configuration.

Any surveys, web forms, and landing pages to be developed are managed through Adobe Campaign fully hosted in the cloud.  If required, an additional subdomain may be delegated to Adobe (for example, web.customer.com) to use for any web components within the tool.  Please note that the subdomain must be unique and can’t be used by another party (for example, an existing ESP or MSP).

| Delegated subdomain | DNS instructions |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.</br>`<subdomain>` NS b.ns.campaign.adobe.com.</br>`<subdomain>` NS c.ns.campaign.adobe.com.</br>`<subdomain>` NS d.ns.campaign.adobe.com. |

>[!NOTE]
>
>By default any web components in the tool will use the initial subdomain delegated to be used for email.

## Cloud messaging deployment (optional)

In the case that the Adobe Campaign Classic marketing instance is hosted on premise at the customer, additional technical configurations will need to be made by the customer.

Any surveys, web forms, and landing pages to be developed are managed through the Adobe Campaign marketing instance, where the recipient records exist. 

Additional CNAME DNS configuration is required to deploy externally facing web components hosted by the Adobe Campaign marketing instance.  This will allow web components (for example, web.customer.com) to be publicly accessible to the Internet and branded with the customer's domain.

Firewall(s) will also need to be configured to allow access to the Adobe Campaign marketing instance which hosts these web components (on port 80 or 443).

**Best Practice Recommendations:**

The subdomain to host web components will be visible to customers, so be sure to make it properly branded and simple to remember as it may need to be typed in manually, for example: https://web.customer.com.
If any forms need to be hosted on secure pages (HTTPS) addition technical configuration will be required, described below.

| Delegated subdomain | DNS instructions |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME `<internal customer server>` |

## Services Rendered

Following these delegations, the infrastructure put in place by Adobe ensures the following services are carried out for each delegated or CNAME-aliased sending domain:

* Creation of postmaster@ and abuse@ inboxes
* Setup of Feedback loops for the delegated domain
* Upon request, Adobe will also configure a DMARC record as specified. Your Deliverability Consultant can assist with designing a long-term DMARC policy and plan for your sending domains.
Parameters established by Adobe are only valid from the time that the delegation was completed and then verified by Adobe, and remains functional.  All Adobe Campaign Cloud offers include domain name delegation as standard.

## Billing and implementation conditions

* According to the initial contract and the type of package selected, other delegations in addition to those included as standard beyond this initial delegation may be included,
* Beyond these included delegations, additional delegations will be billed,
* The billing method for these additional delegations comes at an extra monthly cost, as specified in the initial contract.

These delegations will be accepted provided that the CLIENT chooses the associated domain names that are dedicated to deliveries via the Adobe Campaign tool, and that the delegation prerequisites detailed in the relevant document are correctly implemented.

## Discontinuation of services

At any moment, the CLIENT will be able to make a written demand to no longer benefit from the delegation services and to take on the necessary DNS configurations themselves.

If this should happen, Adobe will provide the CLIENT with an estimate detailing the number of service days necessary to return back to non-domain-delegation mode.

Adobe will be relieved of any liability for the engagement of the aforementioned Deliverability Rate if the Customer fails to comply with the commitments set out above.

Termination of the Marketing Cloud Service will automatically lead to the end of domain delegations, and DNS maintenance for those domains by Adobe.

## Monitoring subdomains using the Control Panel

Once subdomains are configured for your instance, you can monitor them using the Control Panel.

This allows you to view all the subdomains that you delegated to Adobe Campaign, as well as request renewal of their SSL certificates.

For more on this, refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates).

>[!NOTE]
>
>[Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html) is available to customers using Adobe Managed Services only.
