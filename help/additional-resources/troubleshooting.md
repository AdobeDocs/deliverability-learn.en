---
title: Troubleshooting
description:  Learn how to identify and address deliverability issues.
feature: Additional resources
topics: Deliverability
kt: 
thumbnail: 
doc-type: article
activity: understand
team: ACS
---

# Deliverability troubleshooting {#troubleshooting}

Below are a few best practices that can help to identify and address deliverability issues.

## Identify a deliverability issue {#identify-deliverability-issue}

To identify a possible issue, the elements listed on [that page](/help/ongoing-monitoring.md) may draw your attention.

<!--
Mailing or campaign metrics: unsubscribe, abuse complaint and/or bounce rates are higher than usual.
Subscriber activity: opens, clicks and/or transactions are lower than usual.
Seed accounts show filtered or non-delivered mailings.
-->

## Hypothesize potential causes {#potential-causes}

Ask yourself the following questions to identify the possible causes to your deliverability issue:

* Was there a recent change in list segmentation?
* Have I acquired any new data sources?
* Did I accidentally mail a quarantine file?
* Could the problem be due to my message content?
* Do I mail frequently enough to maintain warm IPs?
* Am I segmenting my mailings by activity/engagement, or sending full-files?
* What is the 'safe' segment on my file in terms of recency?
* Do I have reactivation & reconfirmation strategies in place for segments that are not defined as safe?

## Address the issue {#address-issue}

### Complaints

[Complaints](/help/metrics/complaints.md) are defined by subscribers who report email as a spam by hitting the corresponding button from their inbox.

If your delivery issue was caused by complaints:
* You need to try to determine why recipients are complaining.
* You may also want to consider moving your unsubscribe link to the top of your email. This will encourage subscribers to unsubscribe instead of complaining with the spam button.

Senders can glean a wealth of information from their [feedback loop](/help/transition-process/infrastructure.md#feedback-loops) complaints:
* It is important to bucket the data and look for patterns in things like opt-in source, how long the address has been subscribed, or even certain behavioral demographics.
* Complaints can often identify a risky data source or segment within the file. Risky is defined as most likely to complain, which can damage reputation, and in turn, inbox rates.

Complaints also stem from subscribers who just no longer want to receive email:
* This can often be due to over-messaging, your subscribers' perception of the message, that they were not expecting the message, or do not recall opting in.
* It is also important to run an audit to ensure that all points of collection are clear, and that there are no pre-checked boxes in your points of acquisition.
* You should also send a welcome email when subscribers opt-in to set the tone and explain how often they can expect to receive emails from you.

### Data validity

**Hard bounces** occur when you send to an **undeliverable address** at an ISP. An address can be undeliverable for many reasons such as:
* Misspelled address. This can be addressed with a real-time data validation service, or by requiring a confirmed opt-in before sending marketing emails to that address.
* Bad list or data source. If it comes from a new source, review how the addresses were collected and ensure that there was permission.
* Mailing to an address that was at one time active, but has been closed or terminated after a period of inactivity.

### Engagement

In addition to complaints and data validity, ISPs are concentrating more than ever on **positive engagement** to make delivery decisions. They are looking to see whether your subscribers are opening your emails, or deleting them without reading them. Because they don’t share this data with senders, we must utilize the information that we have available and translate opens/clicks/transactions as engagement. 

As part of ongoing reputation maintenance, it is important to understand how engaged subscribers are on your list and develop a **recency risk hierarchy** for the subscribers on each file. Recency is defined as last open/click/transact or sign-up date. This time-frame may differ by vertical. To do this:

1. Determine active (‘safe’) segments for each vertical. This is typically subscribers who have been active within the last 3-6 months.
1. Reduce frequency to inactives.
1. Create a [re-engagement](/help/additional-resources/re-engagement.md) series for moderate risk inactives. This is typically 6-9 months without engagement.
1. Develop a reconfirmation campaign for higher risk inactives. This is typically subscribers who haven’t engaged with an email in 9-12 months.
1. Finally, set a drop-off rule and remove subscribers who haven’t opened your emails in 'x' months. We typically recommend 12+ months, but this can differ based on sales and buying cycle.