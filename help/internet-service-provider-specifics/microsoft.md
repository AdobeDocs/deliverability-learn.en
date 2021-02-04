---
title: Microsoft (Hotmail, Outlook, Windows Live etc.)
description: Microsoft is generally the second- or third- largest provider depending on the makeup of your list, and they do handle traffic slightly different from other ISPs.
feature: ISPs
topics: Deliverability
kt: 5319
doc-type: article
activity: understand
team: TM
---

# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live], etc.) 

[!DNL Microsoft] is generally the second- or third- largest provider depending on the makeup of your list, and they do handle traffic slightly different from other ISPs.

Here are some highlights:

## What data is important

[!DNL Microsoft] focuses on sender reputation, complaints, user engagement, and their own group of trusted users (also known as Sender Reputation Data or SRD) who they poll for feedback.

## What data do they make available

[!DNL Microsoft]’s proprietary sender reporting tool, [!DNL Smart Network Data Services] (SNDS), lets you see metrics around how much mail you are sending and how much mail is accepted, as well as complaints and spam traps. Keep in mind that the data shared is a sample and doesn’t reflect exact numbers, but it does best represent how [!DNL Microsoft] views you as a sender. [!DNL Microsoft] doesn’t provide information on their trusted user group publicly, but that data is available through the [!DNL Return Path Certification] program for an additional fee.

## Sender reputation

[!DNL Microsoft] has been traditionally focused on sending IP in their reputation evaluations and filtering decisions. They’re actively working on expanding their sending domain capabilities as well. Both are largely driven by the traditional reputation influencers, like complaints and spam traps. Deliverability can also be heavily influenced by the Return Path Certification program, which does have specific quantitative and qualitative program requirements.

## Insights

[!DNL Microsoft] combines all of their receiving domains to establish and track sending reputation. This includes [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live], and so on, as well as any corporate Office 365 hosted emails. [!DNL Microsoft] can be especially sensitive to fluctuations in volume, so consider applying specific strategies to ramp up and down from large sends as opposed to allowing for volume based sudden changes.

[!DNL Microsoft] is also especially strict during the initial days of IP warming, which generally means most mail gets filtered initially. Most ISPs consider senders innocent until proven guilty. [!DNL Microsoft] is the opposite and considers you guilty until you prove yourself innocent.
