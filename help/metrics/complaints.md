---
title: Complaints
description: Learn about complaints which are registered when a user indicates that an email is unwanted or unexpected.
topics: Deliverability
jira: KT-7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 0343820d-f5af-4b8a-bcab-dbb47ae7aecb
TQID: https://experienceleague.adobe.com/W9G0ZPGeIm5KmVHu5-VuMd-Kb-4x4f7qhBPnpskxqqA
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
    internal-label: Marketo Engage
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
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
