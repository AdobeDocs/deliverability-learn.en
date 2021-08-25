---
title: Starting a new platform
description: Learn more about managing deliverability when starting a new platform with Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 6c9ade01-3052-4311-af80-888294820024
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
