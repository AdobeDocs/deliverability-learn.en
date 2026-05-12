---
title: Bulking and blocking emails
description: Learn why ISPs place email messages in bulk folders or block them.
topics: Deliverability
jira: KT-7051
thumbnail: kt7051.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4b280f90-73b9-4b88-adb8-57b6a46ddad7
TQID: https://experienceleague.adobe.com/mNz7Z6yQjlK7-NShGkgXNR8hp9kKUXDl9nHzMG4j3Q4
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
---
# Bulking and blocking

## Bulking

Bulking is the delivery of mail into the spam or junk folder of an ISP. It is identifiable when a lower-than-normal open rate (and sometimes click rate) is paired with a high delivered rate. The causes for why emails are bulked varies by ISP. In general, though, if messages are being placed in the bulk folder, a flag that influences sending reputation (list hygiene, for example) requires reevaluation. It’s a signal that reputation is diminishing, which is a problem that needs to be corrected immediately before it affects further campaigns. Work with your Adobe deliverability consultant to remedy any bulking issues depending on your situation.

## Blocking

A block occurs when spam indicators reach proprietary ISP thresholds and the ISP begins to block mail (noticeable through bounced mailing attempts) from a sender. There are various types of blocks. Generally, blocks occur specific to an IP address, but they can also occur at the sending domain or entity level. Resolving a block requires specific expertise, so please contact your Adobe deliverability consultant for assistance.

## Blocklisting

A blocklisting occurs when a third-party blocklist manager registers spammer-like behavior associated with a sender. The cause of a blocklist is sometimes published by the blocklisting party. A listing is generally based on IP address, but in more severe cases it can be by IP range or even a sending domain. Resolving a blocklisting should involve support from your Adobe deliverability consultant in order to fully resolve and prevent further listings. Some listings are extremely severe and can cause long-lasting reputation issues that are difficult to resolve. The result of a blocklisting varies by the blocklist but has the potential to impact delivery of all email.

## Additional resources

* Learn more on [Real-time Blackhole Lists](/help/additional-resources/blocklist-databases.md) that maintain databases of IP addresses and domains likely to be used by spammers.
