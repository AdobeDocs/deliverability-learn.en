---
title: Gmail
description: Gmail makes up the largest portion of most senders' email lists. They also tend to treat email a bit differently than everyone else.
topics: Deliverability
jira: KT-5262
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: a7319c85-32b5-4a9e-bee9-24f13630c408
TQID: https://experienceleague.adobe.com/JU2Mswl8hi0LmTN9XQAUn2n0I4Ye4xpdKK5PnPuL9dY
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
# [!DNL Gmail]

[!DNL Gmail] makes up the largest portion of most senders' email lists. They also tend to treat email a bit differently than everyone else.

Here are some highlights:

## What data is important

[!DNL Gmail] is focused on their users' feedback for much of their filtering decisions. While we can't know the secret sauce involved in these decisions, there are common standards that most marketers can monitor. Open and click rates will provide insight into the engagement of your target audience and can be used to drive positive reputation and high inbox placement.

## What data is available

[!DNL Gmail] does provide limited insight into how they view your sending practices through their [!DNL Gmail Postmaster] Tools. This tool allows you a high-level view of your sending IP and domain reputation, authentication results, and complaint issues.

>[!NOTE]
>
>[!DNL Gmail] doesn't display data on all complaints, nor do they facilitate a traditional FBL. Instead, they only provide data in certain circumstances, usually involving both high volumes and very high complaint rates. While keeping complaints to minimum is key to good deliverability, it's natural for some complaints to filter in. If complaints are regularly clocking at zero, it could point to an issue that requires additional investigation.

## Sender reputation

[!DNL Gmail] tracks IP, domain, and even brand reputation. Changing your IP or domain (or both) won't allow you to easily shake a bad reputation. A quick or creative fix may be tempting, but it's much more effective to allocate time and effort to fixing the root of a reputation issue for inbox placement gains.

## Insights

[!DNL Gmail] views engaged subscribers differently than most senders traditionally do. A sender may define an active or engaged list as someone who has opened an email within 30, 90, or 180 days (depending on the business model). [!DNL Gmail], on the other hand, is looking at how often their users interact with your messages.

For instance, if you send 3 emails a week over 90 days, that would be roughly 39 emails. Using the traditional method, if the subscriber opened one of those 39 emails, they're engaged. To [!DNL Gmail], this means they ignored 38 emails and are not engaged. You can get an approximate feel for your own users' engagement levels at [!DNL Gmail] by grading them on open count over the last 10 emails. So a subscriber associated with 7 opens of your last 10 emails is more engaged than someone who opened 2 of the 10. Sending email less often to those users who are less engaged will help you improve your sending reputation at [!DNL Gmail].

[!DNL Gmail] utilizes different tabs for users to distinguish different types of mail. These are *Inbox*, *Social*, and *Promotional*. Even if mail is delivered into the Promotional tab, it's still considered inbox delivery. Users have control to modify their view and tabs.
