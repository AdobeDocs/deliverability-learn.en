---
title: Complaints
description: Learn about complaints which are registered when a user indicates that an email is unwanted or unexpected. 
topics: Deliverability
kt: 7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 0343820d-f5af-4b8a-bcab-dbb47ae7aecb
---
# Complaints

Complaints are registered when a user indicates that an email is unwanted or unexpected. This subscriber action is typically logged through either the subscriber’s email client when they hit the spam button or via a third-party spam reporting system.

## ISP complaint

Most Tier 1 and some Tier 2 ISPs provide a spam reporting method to their users as opt-out and unsubscribe processes have been used maliciously in the past to validate an email address. Adobe Campaign receives these complaints via ISP FBLs. This is established during the setup process for any ISPs that provide FBLs and allows Adobe Campaign to automatically add email addresses that complained to the quarantine table for suppression. Spikes in ISP complaints can be an indicator of poor list quality, less-than-optimal list collection methods, or weak engagement policies. They’re also often noted when content is not relevant.

## Third-party complaints

There are several anti-spam groups that allow for spam reporting at a broader level. Complaint metrics used by these third parties are used to tag email content to identify spam email. This process is also known as fingerprinting. Users of these third-party complaint methods are generally savvier about email, so they can have a greater impact than other complaints may have if left unanswered.

>[!NOTE]
>
>ISPs collect complains and use them to determine the overall reputation of a sender. All complaints should be suppressed and no longer contacted as quickly as possible and in accordance with local laws and regulations.

## Product specific resources

**Adobe Campaign Classic**

* [Tracking indicators](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html#tracking-indicators)

**Adobe Campaign Standard**

* [Complaints report](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html#reporting)
