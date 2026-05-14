---
title: Re-engagement best practices
description: Learn how to improve deliverability through re-engagement strategies.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 30118706-d4c0-4bd8-8c9b-50c26b8374ef
TQID: https://experienceleague.adobe.com/XbAU6Y0r4Ed8W7t71MMNV02jdp2-og04-v-n2lT5m-4
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
    internal-label: Marketo Engage
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
    internal-label: Database
  - id: e2290edd-b061-4880-9d79-dee306cf5aa9
    internal-label: Implementation
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Re-engagement best practices {#re-engagement}

While implementing deliverability, some of the best practices consist in trying to maintain a healthy subscriber base and improve deliverability through re-engagement (or win-back) strategies.

* Maintaining a healthy subscriber base is one of the major aspects to ensure good and consistent delivery. Many deliverability issues arise from poor data practices and maintenance.
* One of the most common issues that marketers face today is inactive subscriber activity (also referred to as low or non-engagement) which can adversely affect delivery of email and low ROI.

>[!NOTE]
>
>For more information on re-engagement campaign strategies and Adobe’s Deliverability services, please contact your Deliverability consultant, or speak with your Adobe Sales agent.

## How do ISPs view non-engagement activity? {#how-do-isps-view-non-engagement-activity-}

For years, ISPs have used engagement feedback metrics from their users to decide where to place messages, or whether at all they should deliver them. User [engagement](/help/engagement.md) consists of both positive and negative feedback and ISPs monitor both on a constant basis. Having no engagement is perhaps one of the main contributors of negative engagement. From a deliverability perspective, consistently sending campaigns to users who show no engagement can also lower the overall reputation of your IP address and domains.

ISPs such as Gmail, Microsoft®, and OATH view non-engagement as unwanted email and start redirecting messages to the spam folder. Also, these subscribers may no longer own the email account, and this can be used as a "recycled" spam trap. This means that the address was invalid for some time and all messages are rejected. If your subscriber management system is not removing "hard bounced" addresses, it's likely mailing to spam traps that can lead to significant delivery issues.

## How should you approach inactivity? {#how-should-you-approach-inactivity-}

Customers who use the Adobe platform can view inactivity within their instance by reviewing the open and click data according to the segment. Since non-engagement can hinder delivery, the first thought can be to remove subscribers from the database. However, this may prove to be a wrong option sometimes. Therefore, a re-engagement (also known as a win-back) strategy is the best recommendation to retain the subscribers that are interested in receiving mail, and gradually phase out those who no longer show activity.

## Do re-engagement campaigns really work? {#do-re-engagement-campaigns-really-work-}

According to a Return Path study, re-engagement campaigns came out with a result of 12% open rate compared to an average 14% for normal campaigns. Although only 24% of subscribers had read the re-engagement campaign, around 45% of them read the subsequent messages. 

![](../../help/assets/deliverability_implementation_1.png)

## How do you create a re-engagement campaign? {#how-do-you-create-a-re-engagement-campaign-}

### Phase 1 {#phase-1}

* The first step is to identify subscribers who have little to no open or click activity, and accordingly segment this group based on a set time frame. The rule of thumb is to review subscribers who have not opened or clicked an email within the last 90 days. However, this varies according to the nature of the business (for example, seasonal sending).
* Another point to keep in mind while defining timeframes is that ISPs and denylist companies consider engagement to be anywhere between 1.5 and 1.8 years. Also, behavioral activities such as purchases and website activity, or other touch points, such as preferences during the sign-up phase or first point of contact.

### Phase 2 {#phase-2}

* Once a segment is defined, the next step is to create a re-engagement campaign that caters to the subscriber according to the metrics that have been identified. Creating a subject line helps increase the interest of the subscriber. According to a Return Path study, subject lines and content that state "We miss you" generate higher response rates than "We want you back".
* An incentive can also be offered for re-engaging with the email. When considering offers with discounts, it is best to use dollar amounts versus percentages. Return Path also suggests doing this as it incurs higher response rates. Finally, performing A/B split tests to review response and success rates is also a useful option.

### Phase 3 {#phase-3}

The next step is to determine the frequency of the re-engagement campaign. Unlike reconfirmation messages, re-engagement campaigns are meant to win the subscriber back with a series of emails over time. The following example provides an example of the frequency.

![](../../help/assets/deliverability_implementation_2.png)

Subscribers that engage with the campaign by following the open or click activity are added back to the engaged list of subscribers.

### Phase 4 {#phase-4}

* The next phase is to identify subscribers who continually show no activity and gradually reduce sending emails to them over a period of time. If there is no activity within the past year, it is good to put the subscribers email subscription on hold. Although they have shown no interest in the email content, there is always a last chance to have them reactivate their subscription by sending a one-time reconfirmation campaign.
* Reconfirmation campaigns are a good way to ask subscribers who are inactive for a long time if they want to remain on the subscription list. When creating the campaign, it is preferable to add a "click here" link so they can confirm the action and verify their address. This way, the action can be recorded in the database. Below is an example of a reconfirmation email:

  ![](../../help/assets/deliverability_implementation_3.png)

  Once the subscriber has taken an action, a landing page with the confirmation of their resubscription can be offered. Below is an example of the landing page:

  ![](../../help/assets/deliverability_implementation_4.png)

## Product-specific resources

**Adobe Campaign**

* [Tracking logs in Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#tracking-logs)
* [Tracking logs in Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/sending-and-tracking-messages/tracking-messages.html#tracking-logs)

**Adobe Customer Journey Management**

* [Message tracking](https://experienceleague.adobe.com/docs/journey-optimizer/using/reporting/message-tracking.html)
