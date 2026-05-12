---
title: Starting a new platform
description: Learn more about managing deliverability when starting a new platform with Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 6c9ade01-3052-4311-af80-888294820024
TQID: https://experienceleague.adobe.com/cQa5nOTSJwxDGX-QkXGez5dpm5N-8I7QZ-LsEW0FRLo
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
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
    internal-label: Database
  - id: d1d0a9cd-295d-4976-8c39-ddae266f240e
    internal-label: Administration
  - id: e2290edd-b061-4880-9d79-dee306cf5aa9
    internal-label: Implementation
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
    internal-label: Resources
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
    internal-label: Administration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Starting a new platform {#starting-new-platform}

Maintaining your domain and IP address reputation is essential when setting up a new platform to use with Adobe Campaign.

## A sensitive step

You should be very careful when starting to send emails on a new platform, because the platform does not have any history of use, and no reputation when the sending IPs have never been used for this purpose.

ISPs are naturally suspicious of IP addresses that have never been used to send email and that suddenly start to send large volumes of email traffic. Indeed, spammers generally use "unknown" IP addresses (addresses that have never been on denylist) to send the largest possible number of messages before detection.

You cannot expect to reach operational speed in terms of output at the very start of the production phase. Furthermore, you should not attempt to send messages at this rate as it might lead the ISPs to block the sending addresses and to severely compromise the rest of the start-up phase.

## Main principles

Below are listed the main principles to be followed when starting up a new platform.

* Configure a dedicated subdomain that is specific to email campaigns sent from Adobe.

* If you have this information, **import invalid addresses into the quarantine table**. 
    Starting a platform often happens when using a list of addresses for the first time and which may not be fully qualified. If you send to invalid addresses or to honeypot addresses, this will contribute to diminishing the reputation of the platform.

    * If you have a list of invalid addresses, it is in your best interests to import it into the quarantine table before sending for the first times. The quarantine table is available through the **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** (Campaign Classic) and **[!UICONTROL Administration > Channels > Quarantines > Addresses]** (Campaign Standard) menus.

    * If, all the same, you wish to requalify the invalid addresses, it is by far preferable to do this once the reputation of the platform is established and bit by bit in order to "dilute" the use of bad addresses over time.

* **Limit the throughput rate** by limiting the number of mtachilds. For more on adjusting such technical setting, contact your Adobe Campaign administrator.

* **Progressively increase the volumes sent** to avoid being marked as spam. Do not target the whole database from the very start, but rather add an extra fraction of the list each time you send. This should enable you to increase the volume at each step while reducing the overall rate of invalid addresses. To ensure smooth development of the start-up phase, you can use waves.

* **Send regularly**. To a certain extent, it is better to send small shots regularly rather than large campaigns sporadically.
* **Pay close attention to the delivery reports**. High error indicators can mean a technical setting is badly configured.

## Additional resources

For more on the principles listed above and their implementation with Adobe Campaign, see the following sections:

* [Increase your email reputation with IP warming](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [All about spam traps](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [Optimize your delivery through quarantines](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identify quarantined addresses for the entire platform](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [Sending using multiple waves](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves)
* [Delivery monitoring](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html#sending-messages)

**Adobe Campaign Standard**

* [Optimize your delivery through quarantines](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identify quarantined addresses for the entire platform](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)
* [Monitoring a delivery](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html)
