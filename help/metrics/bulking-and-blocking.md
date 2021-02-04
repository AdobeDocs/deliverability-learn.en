---
title: Bulking and blocking emails
description: Learn why ISPs place email messages in bulk folders or block them.
feature: Deliverability
topics: 
kt: 5256
doc-type: article
activity: understand
team: ACS
---

# Bulking and blocking

## Bulking

Bulking is the delivery of mail into the spam or junk folder of an ISP. It is identifiable when a lower-than-normal open rate (and sometimes click rate) is paired with a high delivered rate. The causes for why emails are bulked varies by ISP. In general, though, if messages are being placed in the bulk folder, a flag that influences sending reputation (list hygiene, for example) requires reevaluation. It’s a signal that reputation is diminishing, which is a problem that needs to be corrected immediately before it affects further campaigns. Work with your Adobe deliverability consultant to remedy any bulking issues depending on your situation.

## Blocking

A block occurs when spam indicators reach proprietary ISP thresholds and the ISP begins to block mail (noticeable through bounced mailing attempts) from a sender. There are various types of blocks. Generally, blocks occur specific to an IP address, but they can also occur at the sending domain or entity level. Resolving a block requires specific expertise, so please contact your Adobe deliverability consultant for assistance.

## Blocklisting

A blocklisting occurs when a third-party blocklist manager registers spammer-like behavior associated with a sender. The cause of a blocklist is sometimes published by the blocklisting party. A listing is generally based on IP address, but in more severe cases it can be by IP range or even a sending domain. Resolving a blocklisting should involve support from your Adobe deliverability consultant in order to fully resolve and prevent further listings. Some listings are extremely severe and can cause long-lasting reputation issues that are difficult to resolve. The result of a blocklisting varies by the blocklist but has the potential to impact delivery of all email.

## Additional resources

* [Block list databases](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/block-list-databases.html?lang=en#sending-messages)
