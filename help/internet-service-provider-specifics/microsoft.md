---
title: Microsoft (Hotmail, Outlook, Windows Live etc.)
description: Microsoft is generally the second- or third- largest provider depending on the makeup of your list, and they do handle traffic slightly different from other ISPs.
topics: Deliverability
jira: KT-5319
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
TQID: https://experienceleague.adobe.com/pbp5vbHUIHSL9zL9gQf4LpIhEYZI1umEesy3czbJx-4
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
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
---
# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live], etc.) 

[!DNL Microsoft] is generally the second- or third- largest provider depending on the makeup of your list, and they do handle traffic slightly different from other ISPs.

Here are some highlights:

## What data is important

[!DNL Microsoft] focuses on sender reputation, complaints, user engagement, and their own group of trusted users (also known as Sender Reputation Data or SRD) who they poll for feedback.

## What data do they make available

[!DNL Microsoft]'s proprietary sender reporting tool, [!DNL Smart Network Data Services] (SNDS), lets you see metrics around how much mail you are sending and how much mail is accepted, as well as complaints and spam traps. Keep in mind that the data shared is a sample and doesn't reflect exact numbers, but it does best represent how [!DNL Microsoft] views you as a sender. [!DNL Microsoft] doesn't provide information on their trusted user group publicly, but that data is available through the [!DNL Return Path Certification] program for an additional fee.

## Sender reputation

[!DNL Microsoft] has been traditionally focused on sending IP in their reputation evaluations and filtering decisions. They're actively working on expanding their sending domain capabilities as well. Both are largely driven by the traditional reputation influencers, like complaints and spam traps. Deliverability can also be heavily influenced by the Return Path Certification program, which does have specific quantitative and qualitative program requirements.

## Insights

[!DNL Microsoft] combines all of their receiving domains to establish and track sending reputation. This includes [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live], and so on, as well as any corporate Office 365 hosted emails. [!DNL Microsoft] can be especially sensitive to fluctuations in volume, so consider applying specific strategies to ramp up and down from large sends as opposed to allowing for volume based sudden changes.

[!DNL Microsoft] is also especially strict during the initial days of IP warming, which generally means most mail gets filtered initially. Most ISPs consider senders innocent until proven guilty. [!DNL Microsoft] is the opposite and considers you guilty until you prove yourself innocent.
