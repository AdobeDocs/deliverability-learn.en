---
title: Verizon Media Group (Yahoo, AOL, Verizon, etc.)
description: [!DNL Verizon Media Group] is generally one of the top three domains for most B2C lists. They behave somewhat uniquely, as they’ll generally throttle or bulk mail if reputation issues arise.
feature: 
topics: Deliverability
kt: 5320
doc-type: article
activity: understand
team: TM
---

# [!DNL Verizon Media Group] (Yahoo, AOL, Verizon, etc.)

[!DNL Verizon Media Group] is generally one of the top three domains for most B2C lists. They behave somewhat uniquely, as they’ll generally throttle or bulk mail if reputation issues arise.

Here are some highlights:

## What data is important

[!DNL Verizon Media Group] (VMG) has built and maintains their own proprietary spam filters, using a mixture of content and URL filtering and spam complaints. Along with Gmail, they’re one of the early adopting ISPs that filter email by domain as well as IP address.

## What data do they make available

VMG has an FBL used to feed complaint information back to senders. They are also exploring adding more data in the future.

## Sender reputation

A sender’s reputation is made up of a combination of IP address, domain, and from address. Reputation is calculated using the traditional components, including complaints, spam traps, inactive or malformed addresses, and engagement. VMG uses rate limiting (also known as throttling) along with bulk foldering to defend against spam. They complement their internal filtering systems with some [!DNL Spamhaus] black lists, including the PBL, SBL, and XBL to protect their users.

## Insights

VMG has regular maintenance periods for old, inactive, email addresses lately. That means it is common to observe a significant surge in invalid address bounces, which may impact your delivered rate for a short period of time. They are also sensitive to high rates of invalid address bounces from a sender, which is indicative of a need to tighten acquisition or engagement policies. Senders can often experience negative impact at around 1 percent invalid addresses.
