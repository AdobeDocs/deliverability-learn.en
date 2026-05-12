---
title: Verizon Media Group (Yahoo, AOL, Verizon, etc.)
description: "[!DNL Verizon Media Group] is generally one of the top three domains for most B2C lists. They behave somewhat uniquely, as they'll generally throttle or bulk mail if reputation issues arise."
topics: Deliverability
jira: KT-5320
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: 43e6d3cb-23c3-4076-8026-a1a08e76bd1b
TQID: https://experienceleague.adobe.com/ycELLXdqC1E3EIxywp-I1HWnSyWayRHcwkNOzmzSBvY
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
    internal-label: Marketo Engage
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
---
# [!DNL Verizon Media Group] (Yahoo, AOL, Verizon, etc.)

[!DNL Verizon Media Group] is generally one of the top three domains for most B2C lists. They behave somewhat uniquely, as they'll generally throttle or bulk mail if reputation issues arise.

Here are some highlights:

## What data is important

[!DNL Verizon Media Group] (VMG) has built and maintains their own proprietary spam filters, using a mixture of content and URL filtering and spam complaints. Along with Gmail, they're one of the early adopting ISPs that filter email by domain as well as IP address.

## What data do they make available

VMG has an FBL used to feed complaint information back to senders. They are also exploring adding more data in the future.

## Sender reputation

A sender's reputation is made up of a combination of IP address, domain, and from address. Reputation is calculated using the traditional components, including complaints, spam traps, inactive or malformed addresses, and engagement. VMG uses rate limiting (also known as throttling) along with bulk foldering to defend against spam. They complement their internal filtering systems with some [!DNL Spamhaus] black lists, including the PBL, SBL, and XBL to protect their users.

## Insights

VMG has regular maintenance periods for old, inactive, email addresses lately. That means it is common to observe a significant surge in invalid address bounces, which may impact your delivered rate for a short period of time. They are also sensitive to high rates of invalid address bounces from a sender, which is indicative of a need to tighten acquisition or engagement policies. Senders can often experience negative impact at around 1 percent invalid addresses.
