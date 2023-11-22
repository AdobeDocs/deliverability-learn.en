---
title: Guidance around the announced changes at [!DNL Google] and [!DNL Yahoo]
description: Guidance around the announced changes at [!DNL Google] and [!DNL Yahoo]
role: Admin
level: Experienced
doc-type: Article
last-substantial-update: 2023-11-06
jira: KT-14320
thumbnail: KT-14320.jpeg
exl-id: 879e9124-3cfe-4d85-a7d1-64ceb914a460
---
# Guidance around the announced changes at [!DNL Google] and [!DNL Yahoo]

On October 3rd both [!DNL Google] and [!DNL Yahoo] jointly announced planned changes via their blogs. These changes are designed to keep their users safer and provide a better email experience by enforcing some common industry best practices as new requirements starting in February 2024.

[https://blog.google/products/gmail/gmail-security-authentication-spam-protection/](https://blog.google/products/gmail/gmail-security-authentication-spam-protection/){target="_blank"}

![[!DNL Google] Announcement_](/help/assets/Gmail.png)

[https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam](https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam){target="_blank"}

![[!DNL Yahoo] Announcement](/help/assets/Yahoo.png)

The email deliverability experts at Adobe have read through these blog posts and all of the linked documentation so that you don't have to. Here are the key takeaways.

## So, what exactly are [!DNL Google] and [!DNL Yahoo] doing?

In the world of email there are legal requirements, practical requirements, and general best practices. Legal requirements vary widely from location to location and are not part of this topic. Instead, [!DNL Google] and [!DNL Yahoo] are taking best practices and turning them into practical requirements. None of the items [!DNL Google] and [!DNL Yahoo] are going to start requiring in February are new, and have often been best practice recommendations for years, but adoption has been slow and uneven in the industry. This is [!DNL Google] and [!DNL Yahoo]'s way of helping progress that adoption process by saying "If you want to deploy email to our users (this may represent a significant portion of your email list, in some cases as high as 70%, depending on region and industry) you need to do these things."

## What are the details?

If you are an Adobe customer most of what they are requiring is already part of your setup, but there are a few key items that are technically optional, and you will want to be certain your organization has adopted and setup these items correctly before February 2024.

## DMARC:

[!DNL Google] and [!DNL Yahoo] will both be requiring that you have a DMARC record for any domain you use to send email to them. They are NOT currently requiring a p=reject or p=quarantine setting, so a setting of p=none, commonly called the "monitoring" setting, is perfectly acceptable. This will not change how your emails are processed, they will do what they would normally do without DMARC. Setting this up is the first step to protecting yourself with DMARC, and in addition to the new benefit of helping you send email to [!DNL Google] and [!DNL Yahoo] it can also help you see if there are authentication issues anywhere within your email eco-system.
DMARC is fully supported in Adobe currently but is not required. Use any free DMARC checker to see if you have DMARC setup for your subdomains, and if you do not, talk to your Adobe support team to see how best to go about getting that setup. 

You can also find more information about DMARC and how to implement it [here](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html){target="_blank"} for Adobe Campaign and Adobe Journey Optimizer Adobe or [here](https://experienceleague.adobe.com/docs/marketo/using/getting-started-with-marketo/setup/configure-protocols-for-marketo.html){target="_blank"} for Marketo Engage.

## 1-Click (List) Unsubscribe:

Don't panic. [!DNL Google] and [!DNL Yahoo] are not talking about the unsubscribe links in your email body or footer that might be clicked on by a security bot just doing its job or by accident. What they mean is the List-Unsubscribe header functionality for either the "mailto" or "http/URL" versions. This is the function within the [!DNL Yahoo] and Gmail UIs where users can click unsubscribe. Gmail even prompts users who click on "Report Spam" to see if they meant to unsubscribe instead, which can reduce the number of complaints you get (complaints hurt your reputation) by turning them into unsubscribes instead (doesn't hurt your reputation).
It is important to note that [!DNL Google] and [!DNL Yahoo] are both referring to the "http/URL" option by the name "1-Click", and this is intentional. Technically the original "http/URL" option allowed you to redirect recipients to a website. That is not the focus of [!DNL Yahoo] and [!DNL Google], who both reference the updated RFC8058 which focuses on processing the unsubscribe via an HTTPS POST request instead of a website, making it "1-Click".
For Marketo Engage, Adobe has already enabled the "mailto" option and does not currently support the "http/URL" option. Further updates on that to come.
For Adobe Campaign and Adobe Journey Optimizer Adobe recommends using both "mailto" and "1-Click" options.

The need for list-unsubscribe headers does not apply to transactional emails. Please note that triggered messages such as Abandoned Cart and similar communications not generated by the subscriber are considered marketing by mailbox providers like [!DNL Google] and [!DNL Yahoo] and those would need list-unsubscribe.

>[!INFO]
> For more information about how to implement list-unsubscribe for your solution please check:
> * [!DNL Adobe Campaign Classic]: [Technical recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=en#list-unsubscribe){target="_blank"} 
>* [!DNL Adobe Campaign Standard]: [What is the List-Unsubscribe header? And how can this be implemented in ACS?](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-14778.html?lang=en){target="_blank"}
>* [!DNL Adobe Journey Optimizer]: [Email opt-out management](https://experienceleague.adobe.com/docs/journey-optimizer/using/email/email-opt-out.html?lang=en){target="_blank"}
>
> Or reach out to Adobe Customer Support team at any time.


## Process Unsubscribes within 2 days:

This has been a recommended best practice for a while, as every email you deploy to someone who unsubscribed typically results in a spam complaint, so the sooner you stop sending them email the better. Again, legal requirements may be a lot longer in some cases, but [!DNL Google] and [!DNL Yahoo] will know that their user unsubscribed via List-Unsubscribe and that you are still sending them email on day 3, and they have stated they will not allow senders who do that to continue sending email to ANY of their users.
This 2-day requirement is for any unsubscribe through the various list-unsubscribe methods. In some cases (like "mailto") that means Adobe will process them. Adobe processes all unsubscribe requests immediately upon receipt of the request, well within the 2-day limit. In other cases you may be processing them. If you are processing these requests you may need to make changes on your end to meet this 2-day timeline.

## Complaint Rates:

Keeping low complaint rates under 0.2% has been a best practice for a long time. [!DNL Google] is setting the bar higher at 0.3% over an extended period of time but has clearly stated there are benefits to keeping it under 0.1%. Here are the details they shared:

* Aim to keep your spam rate below 0.10%.
* Avoid a spam rate of 0.30% or higher, especially for any sustained period of time.
* Maintaining a low spam rate makes senders more resilient to occasional spikes in user feedback.
* Similarly, maintaining a high spam rate will lead to increased spam classification. It can take time for improvements in spam rate to reflect positively on spam classification.
[!DNL Yahoo] has stated that their complaint threshold will be in the 0.30% range as well.

If you need assistance monitoring your complaint rates, or would like help with strategies to reduce complaints, please talk with your Adobe Deliverability Consultant, or speak with your account team about adding a Deliverability Consultant if you do not already have one.

## How will this impact me as a marketer?

Failing to stick to these new requirements from Gmail and [!DNL Yahoo] is expected to result in emails landing into the spam folder or getting blocked (i.e., getting a bounce back from the MBP indicating the email was not delivered).
As such, Adobe strongly recommends you go through the changes outlined above and ensure you start complying with them as soon as possible. Now is also a great time to start benchmarking your performance at [!DNL Yahoo] and [!DNL Google] to allow you to see if there is any material change to your metrics come February.
We are here to help, so if you have any questions or need support, please talk with your Adobe Deliverability Consultant or speak with your account team about adding a Deliverability Consultant if you do not already have one.

## Are there ways around this?

While this is always a question that comes up, the reality is that these changes make sense for the end users of [!DNL Google] and [!DNL Yahoo]'s platforms. They are motivated by those users' expectations to enforce these rules. We do not recommend trying to circumvent any of these changes, but rather take a step back and think about how to accommodate these changes.
