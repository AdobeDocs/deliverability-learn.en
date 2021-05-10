---
title: Volume - Tips for how to transition smoothly
description: The volume of mail you’re sending is critical to establishing a positive reputation. Learn what you can do to transition smoothly.
feature: Transition Process
topics: Deliverability
kt: 7055
thumbnail: kt7055.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 1bc56061-0c64-4033-b49c-66618916bca6
---
# Volume

The volume of mail you’re sending is critical to establishing a positive reputation. Put yourself in an ISPs shoes — if you start seeing a ton of traffic from someone you don’t know, it would be alarming. Sending large volume of mail right away is risky and is sure to cause reputation issues that are often difficult to resolve. It can be frustrating, time consuming, and costly to dig yourself out of poor reputation and bulking and blocking issues resulting from sending too much too soon.

The volume thresholds vary by ISP and can also vary depending on your average engagement metrics. Some senders require a very low and slow ramp of volume, whereas others may allow for a steeper ramp in volume. We recommend working with an expert, like an Adobe deliverability consultant, to develop a customized volume plan.

Here’s a list of hints and tips for how to transition smoothly:

* **Permission** is the foundation of any successful email program.
* **Low and slow** — start with low sending volumes and then increase as you establish your sender reputation.
* A **tandem mailing strategy** allows you to ramp up volume on Campaign while winding down with your current ESP, without disrupting your email calendar.
* **Engagement matters** — start with the subscribers who open and click your emails regularly.
* **Follow the plan** — our recommendations have helped hundreds of Campaign clients successfully ramp up their email programs.
* **Monitor your reply email account**. It’s a bad experience for your customer to use noreply@xyz.com or to not respond.
* Inactive addresses can have a negative deliverability impact. **Reactivate and repermission on your current platform**, not your new IPs.
* **Domains** — use a sending domain that’s a subdomain of your company’s actual domain
  * For example, if your company domain is xyz.com, email.xyz.com provides more credibility to the ISPs than xyzemail.com
* **Transparency** — registration details for your email domain should be available publicly and shouldn’t be private.

In many circumstances, transactional mail doesn’t follow the traditional promotional warming approach. It’s obviously difficult to control volume in transactional mail due to its nature, since it generally requires a user interaction to trigger the email touch. In some cases, transactional mail can simply be transitioned without a formal plan. In other cases, it might be better to transition each message type over time to slowly grow the volume. For example, you may want to transition as follows:

1. Purchase confirmations — high engagement generally
2. Cart abandon—medium - high engagement generally
3. Welcome emails — high engagement but can contain bad addresses depending on your list collection methods
4. Winback emails — lower engagement generally

## Product specific resources

**Campaign**

* Learn more about managing deliverability when starting a new platform with Adobe Campaign in [this section](/help/additional-resources/ac-starting-new-platform.md).
* Learn how to send using multiple waves with Adobe Campaign Classic in [this section](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves).
* Learn how to fully delegate a subdomain to Adobe Campaign Classic or Standard in [this section](/help/additional-resources/ac-domain-name-setup.md).
* [Control Panel: Full subdomain delegation (tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Learn how to fully delegate a subdomain to Adobe Campaign Classic.*
* [Control Panel: Full subdomain delegation (tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Learn how to fully delegate a subdomain to Adobe Campaign Standard.*

## Additional resources

* Learn more on increasing your email reputation with IP warming in [this section](/help/additional-resources/increase-reputation-with-ip-warming.md).
