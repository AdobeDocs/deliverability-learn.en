---
title: Other metrics that matter for deliverability
description: One of the best ways to identify a sending reputation issue is through the metrics. Understand which key deliverability metrics to monitor and how to use them to identify a reputation issue.
feature: Deliverability
topics: 
kt: 5256
doc-type: article
activity: understand
team: ACS
---

# Other metrics that matter for deliverability

One of the best ways to identify a sending reputation issue is through the metrics. Let’s take a look at some key deliverability metrics to monitor and how to use them to identify a reputation issue.

## Bounces

Bounces are the result of a delivery attempt and failure where the ISP provides back failure notices. Bounce handling processing is a critical part of list hygiene. After a given email has bounced several times in a row, this process flags it for suppression. The number and type of bounces required to trigger suppression vary from system to system. This process prevents systems from continuing to send invalid email addresses. Bounces are one of the key pieces of data that ISPs use to determine IP reputation. Keeping an eye on this metric is very important. “Delivered” versus “bounced” is probably the most common way of measuring the delivery of marketing messages: the higher the delivered percentage is, the better.

We’ll dig into two different kinds of bounces.

### Hard bounces

Hard bounces are permanent failures generated after an ISP determines a mailing attempt to a subscriber address as not deliverable. Within Adobe Campaign, hard bounces that are categorized as undeliverable are added to the quarantine, which means they wouldn’t be reattempted. There are some cases where a hard bounce would be ignored if the cause of the failure is unknown.
Here are some common examples of hard bounces:

* Address doesn’t exist
* Account disabled
* Bad syntax
* Bad domain
  
### Soft bounces

Soft bounces are temporary failures that ISPs generate when they have difficulty delivering mail. Soft failures will retry multiple times (with variance depending on use of custom or out-of-box delivery settings) in order to attempt a successful delivery. Addresses that continually soft bounce will not be added to quarantine until the maximum number of retries has been attempted (which again vary depending on settings). Some common causes of soft bounces include the following:

* Mailbox full
* Receiving email server down
* Sender reputation issues

![bounce types](assets/bounce-types.png)

>[!NOTE]
>
>Bounces are a key indicator of a reputation issue because they can highlight a bad data source (hard bounce) or a reputation issue with an ISP (soft bounce).
>
>Soft bounces often occur as part of sending email and should be allowed to resolve during the retry processing before characterizing as a true deliverability issue. If your soft bounce rate is greater than 30 percent for a single ISP and do not resolve within 24 hours, it’s a good idea to raise a concern with your Adobe Campaign deliverability consultant.

## Complaints

Complaints are registered when a user indicates that an email is unwanted or unexpected. This subscriber action is typically logged through either the subscriber’s email client when they hit the spam button or via a third-party spam reporting system.

### ISP complaint

Most Tier 1 and some Tier 2 ISPs provide a spam reporting method to their users as opt-out and unsubscribe processes have been used maliciously in the past to validate an email address. Adobe Campaign receives these complaints via ISP FBLs. This is established during the setup process for any ISPs that provide FBLs and allows Adobe Campaign to automatically add email addresses that complained to the quarantine table for suppression. Spikes in ISP complaints can be an indicator of poor list quality, less-than-optimal list collection methods, or weak engagement policies. They’re also often noted when content is not relevant.

### Third-party complaints

There are several anti-spam groups that allow for spam reporting at a broader level. Complaint metrics used by these third parties are used to tag email content to identify spam email. This process is also known as fingerprinting. Users of these third-party complaint methods are generally savvier about email, so they can have a greater impact than other complaints may have if left unanswered.

>[!NOTE]
>
>ISPs collect complains and use them to determine the overall reputation of a sender. All complaints should be suppressed and no longer contacted as quickly as possible and in accordance with local laws and regulations.

## Spam traps

Spam traps exist to help identify mail from fraudulent senders or those that aren’t following email best practices. The spam trap email address is generally not publicly published and are almost impossible to identify. Delivering email to spam traps can impact your reputation with varying degrees of severity depending on the type of trap and the ISP. Learn more about the different types of spam traps in the following sections.

### Recycled

Recycled spam traps are addresses that were once valid but are no longer being used. One key way to keep lists as clean as possible is to regularly send email to your entire list and appropriately suppress bounced emails. This helps abandoned email addresses to be quarantined and withheld from further use.

In some cases, an address can become recycled within 30 days. Sending regularly is a vital aspect of good list hygiene, along with regularly suppressing inactive users. **Reengagement campaigns** are typically a part of sophisticated email marketing programs. This campaign style allows the sender to attempt to win back users that would otherwise no longer be mailed.

### Typo

A typo spam trap is an address that contains a misspelling or malformation. This often occurs with known misspellings of major domains like Gmail (ex: gmial is a common typo). ISPs and other blocklist operators will register known bad domains to be used as a spam trap in order to identify spammers and measure sender health. The best way to prevent typo spam traps is to use a **double opt-in process** for list collection.

### Pristine

A pristine spam trap is an address that has no end user and has never had an end user. It’s an address that was created purely to identify spam email. This is the most impactful type of spam trap as it is virtually impossible to identify and would require a substantial effort to clean from your list. Most blocklists utilize pristine spam traps to list unreputable senders. The only way to avoid pristine spam traps from infecting your broader marketing email list is to utilize a **double opt-in process** for list collection.

## Bulking

Bulking is the delivery of mail into the spam or junk folder of an ISP. It is identifiable when a lower-than-normal open rate (and sometimes click rate) is paired with a high delivered rate. The causes for why emails are bulked varies by ISP. In general, though, if messages are being placed in the bulk folder, a flag that influences sending reputation (list hygiene, for example) requires reevaluation. It’s a signal that reputation is diminishing, which is a problem that needs to be corrected immediately before it affects further campaigns. Work with your Adobe deliverability consultant to remedy any bulking issues depending on your situation.

## Blocking

A block occurs when spam indicators reach proprietary ISP thresholds and the ISP begins to block mail (noticeable through bounced mailing attempts) from a sender. There are various types of blocks. Generally, blocks occur specific to an IP address, but they can also occur at the sending domain or entity level. Resolving a block requires specific expertise, so please contact your Adobe deliverability consultant for assistance.

## Blocklisting

A blocklisting occurs when a third-party blocklist manager registers spammer-like behavior associated with a sender. The cause of a blocklist is sometimes published by the blocklisting party. A listing is generally based on IP address, but in more severe cases it can be by IP range or even a sending domain. Resolving a blocklisting should involve support from your Adobe deliverability consultant in order to fully resolve and prevent further listings. Some listings are extremely severe and can cause long-lasting reputation issues that are difficult to resolve. The result of a blocklisting varies by the blocklist but has the potential to impact delivery of all email.

## Additional resources

Adobe Campaign Standard
* [Delivery failure types and reasons](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=en#delivery-failure-types-and-reasons)
* [Double opt-in process](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=en#communication-channels)
* [Monitoring deliverability](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/managing-deliverability/monitor-deliverability.html)
