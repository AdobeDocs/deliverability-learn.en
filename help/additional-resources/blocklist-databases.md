---
title: Real-time Blackhole Lists
description: Learn about organizations which maintain lists of IP addresses and domains likely to be used by spammers.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4155b89f-a636-404c-8951-563c1b4d0289
TQID: https://experienceleague.adobe.com/dsyoiAT3fYro3L8HkRT6OuXGfBqaVOJNy-IoFXQK37I
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
    internal-label: Marketo Engage
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
    internal-label: Database
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
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
---
# Real-time Blackhole Lists

Several organizations maintain databases of IP addresses and domains that are reputed to be used by spammers. Consulting these sites can be useful to understand why certain messages were rejected as spam. It is generally possible to request the removal of an address erroneously added to these lists.

These databases are called RBLs (Real-time Blackhole Lists) and they are consulted via a DNS mechanism. There are three types of RBLs:

* By IP address: lists IP addresses sending spam or likely to be relaying spam.
* By sender domain: lists sender domains (full domain of the bounce mail address) sending spam or incorrectly configured.
* By web domain: lists the domains (high-level domains as registered with the registrars) found in the URLs of the links and images contained in spam content. In Adobe solutions, the domain to be considered is generally the address used for tracking.

The following is a list of the most widely used RBLs. For a more comprehensive list, you can refer to [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

  Refer to [https://www.spamhaus.org/](https://www.spamhaus.org/)

  The database is more important. Being classified on this list is generally a serious situation. If this happens, you must act IMMEDIATELY and warn commercial services, deliverability, and [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

  Refer to [https://www.spamcop.net/](https://www.spamcop.net/)

  It is one of the most renowned databases. If one of your IP addresses is placed on this list, this generally means that the SpamCop users have declared your messages as being Spam or that you have sent messages to a SpamCop honeypot.
    
* **URIBL**

  Refer to [https://www.uribl.com/](https://www.uribl.com/)

  This list identifies the domains that regularly appear in messages declared as spam. If your domain appears on this list, it can significantly affect your deliverability. You should inform the deliverability services and [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) immediately.

* **SURBL**

  Refer to [https://surbl.org/](https://surbl.org/)

  SURBL identifies the websites that regularly appear in spam. If your domain appears on this list, it can significantly affect your deliverability. You should inform the deliverability services and [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) immediately.

* **iX Manitu**

  This is a list of IPs and is widely used in Germany. Refer to [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--
* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.
-->
