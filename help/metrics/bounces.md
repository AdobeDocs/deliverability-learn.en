---
title: Bounces
description: Learn about the different types of bounces
feature: Metrics
topics: Deliverability
kt: 7047
doc-type: article
activity: understand
team: ACS
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
>Soft bounces often occur as part of sending email and should be allowed to resolve during the retry processing before characterizing as a true deliverability issue. If your soft bounce rate is greater than 30 percent for a single ISP and do not resolve within 24 hours, it’s a good idea to raise a concern with your Adobe Campaign deliverability consultant.

## Product specific resources

**Adobe Campaign Standard**

* [Bounce summary](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=en#reporting)
* [Understanding delivery failures](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=en#about-delivery-failures)

**Adobe Campaign Classic**

* [Understanding delivery failures](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=en#sending-messages)