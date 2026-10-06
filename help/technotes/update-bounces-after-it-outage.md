---
title: Update bounce qualification after Italia Online outage
description: Learn how to update bounce qualification after Italia Online outage
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
role: Admin
level: Beginner
TQID: 'https://experienceleague.adobe.com/hPHB9s3PH7E9L3omZMTWZA2ZB0d1JS5vEfawQOjnBLw'
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
  - id: b3b8a63f-51fc-40f6-a7d2-a31c5d49fb45
    internal-label: Configuration
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
    internal-label: Resources
  - id: 63876777-85c3-57e1-a2da-81f02956c63c
    internal-label: Deliverability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
---
# Update incorrect hard bounces after Italia Online outage {#update-bounce-italia}

## Context{#outage-context}

Starting January 22nd (local time), Italia Online has gone through an outage that has resulted on several delays and rejected emails. The service started to resume with limited capacity on Jan 26th. 

Impacted domains are: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it**, and **blu.it**.

This issue occurred from 1/22/2023 to 1/26/2023, but most of the wrongly quarantines happened on Jan 26. 

Learn more in the official communication [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impact{#outage-impact}

As in most of the cases when there is an outage of an Internet Service Provider (ISP), some emails sent through Campaign or Journey Optimizer were wrongly marked as bounces. This was not only impacting Adobe, but everyone trying to get email delivered to Italia Online during the duration of the outage.

Symptoms were:

* **Soft bounces** with the message `452 requested action aborted: try again later` – these were automatically retried, and no actions are needed.

* **Hard bounces** with the message `550 <email address> recipient rejected` have been returned by the ISP on January 26th, between 8am – 2pm local time, to prevent senders to keep overloading their servers. As confirmed by the Italia Online Postmaster, these are not real hard bounces, so we recommend to un-quarantine all the email addresses that got excluded on January 26, 2023 due to that message.

## Process to update{#outage-update}

### Adobe Campaign{#ac-update}

Per standard bounce handling logic, Adobe Campaign automatically added these recipients to the quarantine list with a **[!UICONTROL Status]** setting of **[!UICONTROL Quarantine]**. To correct this, you need to update your quarantine table in Campaign by finding and removing these recipients, or changing their **[!UICONTROL Status]** to **[!UICONTROL Valid]** so that the nightly clean-up workflow will remove them. 

To find the recipients who were affected by this issue, or in case this happens again with any other ISP, please see the instructions below:

* For Campaign Classic v7 and Campaign v8, refer to [this page](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* For Campaign Standard, refer to [this page](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.

### Adobe Journey Optimizer{#ajo-update}

Per standard bounce handling logic, Adobe Journey Optimizer automatically added these email addresses to the suppression list with a **[!UICONTROL Reason]** setting of **[!UICONTROL Invalid Recipient]**. To correct this, you need to update the suppression list by finding and removing these email addresses. 

Once identified, these addresses can be manually removed from the suppression list using the **[!UICONTROL Delete]** button. These addresses can then be included in future email campaigns. 

Learn more in [this section](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html#remove-from-suppression-list){_blank}.

