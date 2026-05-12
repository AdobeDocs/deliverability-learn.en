---
title: Bounces
description: Learn about the different types of bounces.
topics: Deliverability
jira: KT-7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 6338eb67-3efd-476e-8b26-97bbb6a1d35f
TQID: https://experienceleague.adobe.com/0Gly4dAgTpfrmnFD3N-RphZf9vmctJ57fMi1hSmfMTg
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
# Bounces

Bounces are the result of a delivery attempt and failure where the ISP provides back failure notices. Bounce handling processing is a critical part of list hygiene. After a given email has bounced several times in a row, this process flags it for suppression. The number and type of bounces required to trigger suppression vary from system to system. This process prevents systems from continuing to send invalid email addresses. Bounces are one of the key pieces of data that ISPs use to determine IP reputation. Keeping an eye on this metric is very important. “Delivered” versus “bounced” is probably the most common way of measuring the delivery of marketing messages: the higher the delivered percentage is, the better.

We will dig into two different kinds of bounces.

## Hard bounces

Hard bounces are permanent failures generated after an ISP determines a mailing attempt to a subscriber address as not deliverable. Within Adobe Campaign, hard bounces that are categorized as undeliverable are added to the quarantine, which means they wouldn’t be reattempted. There are some cases where a hard bounce would be ignored if the cause of the failure is unknown.
Here are some common examples of hard bounces:

* Address doesn’t exist
* Account disabled
* Bad syntax
* Bad domain
  
## Soft bounces

Soft bounces are temporary failures that ISPs generate when they have difficulty delivering mail. Soft failures will retry multiple times (with variance depending on use of custom or out-of-box delivery settings) in order to attempt a successful delivery. Addresses that continually soft bounce will not be added to quarantine until the maximum number of retries has been attempted (which again vary depending on settings). Some common causes of soft bounces include the following:

* Mailbox full
* Receiving email server down
* Sender reputation issues

![bounce types](../assets/bounce-types.png)

>[!NOTE]
>
>Bounces are a key indicator of a reputation issue because they can highlight a bad data source (hard bounce) or a reputation issue with an ISP (soft bounce).
>
>Soft bounces often occur as part of sending email and should be allowed to resolve during the retry processing before characterizing as a true deliverability issue. If your soft bounce rate is greater than 30 percent for a single ISP and does not resolve within 24 hours, it’s a good idea to raise a concern with your Adobe Campaign deliverability consultant.

## Product specific resources

**Adobe Campaign Classic**

* [Delivery failure types and reasons](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#delivery-failure-types-and-reasons)
* [Bounce mail management](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#bounce-mail-management)
* [Non-deliverables and bounces report](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/global-reports.html#non-deliverables-and-bounces)

**Adobe Campaign Standard**

* [Delivery failure types and reasons](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html#delivery-failure-types-and-reasons)
* [Bounce mail qualification](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html#bounce-mail-qualification)
* [Bounce summary report](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=en#reporting)
