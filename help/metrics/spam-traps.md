---
title: Spam traps
description: Learn about the different types of spam traps.
feature: Metrics
topics: Deliverability
kt: 7050
thumbnail: kt7050.jpg
doc-type: article
activity: understand
team: ACS
---

# Spam traps

Spam traps exist to help identify mail from fraudulent senders or those that aren’t following email best practices. The spam trap email address is generally not publicly published and are almost impossible to identify. Delivering email to spam traps can impact your reputation with varying degrees of severity depending on the type of trap and the ISP. Learn more about the different types of spam traps in the following sections.

## Recycled

Recycled spam traps are addresses that were once valid but are no longer being used. One key way to keep lists as clean as possible is to regularly send email to your entire list and appropriately suppress bounced emails. This helps abandoned email addresses to be quarantined and withheld from further use.

In some cases, an address can become recycled within 30 days. Sending regularly is a vital aspect of good list hygiene, along with regularly suppressing inactive users. **Re-engagement campaigns** are typically a part of sophisticated email marketing programs. This campaign style allows the sender to attempt to win back users that would otherwise no longer be mailed.

## Typo

A typo spam trap is an address that contains a misspelling or malformation. This often occurs with known misspellings of major domains like Gmail (ex: gmial is a common typo). ISPs and other blocklist operators will register known bad domains to be used as a spam trap in order to identify spammers and measure sender health. The best way to prevent typo spam traps is to use a **double opt-in process** for list collection.

## Pristine

A pristine spam trap is an address that has no end user and has never had an end user. It’s an address that was created purely to identify spam email. This is the most impactful type of spam trap as it is virtually impossible to identify and would require a substantial effort to clean from your list. Most blocklists utilize pristine spam traps to list unreputable senders. The only way to avoid pristine spam traps from infecting your broader marketing email list is to utilize a **double opt-in process** for list collection.

## Additional resources

* Learn more on identifying and avoiding spam traps in [this section](/help/additional-resources/all-about-spam-traps.md).
* Learn more on how to improve deliverability through re-engagement strategies in [this section](/help/additional-resources/re-engagement.md).

## Product specific resources

**Adobe Campaign Classic**

* [SpamAssassin](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/spamassassin.html?lang=en#using-spamassassin)
* [Create a subscription form with double opt-in](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=en#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Preview your email and anti-spam analysis](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/designing-content/email-designer/preview-your-email.html#designing-content)
* [Double opt-in process](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=en#communication-channels)
  