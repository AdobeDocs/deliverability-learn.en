---
title: What is the deliverability strategy and how to define deliverability
description: Understand how deliverability is defined, why it matters and the key deliverability metrics.
topics: Deliverability
kt: 5255
thumbnail: kt5255.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 5285eda9-5099-48d5-b150-ce2c376ee549
---
# Deliverability strategy and definition

Designing successful email marketing campaigns depends on having a clear understanding of marketing goals, whether they’re for prospecting or customer relationship management (CRM) initiatives. This helps to determine who to target, what to promote, and when outreach is ideal.

Here are some examples of email marketing strategy objectives:

* Acquiring new customers
* Converting prospects to first time buyers
* Growing current customer relationships with additional client offerings
* Retaining loyal customers
* Enhancing customer satisfaction and brand loyalty
* Reactivating lost or lapsed customers

## Deliverability defined

There are two key metrics that play a role in the definition of deliverability. The *delivered rate* is the percentage of emails that don’t bounce and are accepted by the ISP. Next is *inbox placement* — this is applied to the messages that are accepted by the ISP and determines whether the email lands in the inbox or the spam folder.

It is important to understand both delivered rate and the inbox placement rate in conjunction with one another when measuring email performance. A high delivered rate is not the only facet of deliverability. Just because a message is received via an ISP’s initial checkpoint doesn’t necessarily mean that your subscriber actually saw and interacted with your communication.

## Why deliverability matters

If you don’t know whether your emails are getting delivered or whether they are landing in the inbox versus the spam folder, you should. Here’s why.

Countless hours go into the planning and production of your email campaigns. If the emails bounce or ultimately land in your subscribers’ spam folder, your customers probably won’t read them, your call to action (CTA) won’t be acknowledged, and you’ll fall short of your revenue goals due to lost conversions. Put simply, you can’t afford to ignore deliverability. It is crucial to the success of your email marketing efforts and your bottom line.

Following deliverability best practices ensures that your email will have the best possible chance of opens, clicks, and the ultimate goal - conversion. You can write a brilliant subject line and have beautiful imagery and engaging content. But if that email doesn’t get delivered, the customer doesn’t have any opportunity to convert. All in all, in email deliverability, each step in the mail acceptance process is dependent on the former for program success.

### Step 1: Email delivered

Important factors for delivery:

* **Solid infrastructure**: IP and domain configuration, feedback loop (FBL) setup (including complaint monitoring and processing), and regular bounce processing. For Adobe clients, Adobe is responsible for this setup on behalf of our clients.
* **Strong authentication**: [!DNL Sender Policy Framework] (SPF), [!DNL DomainKeys Identified Mail] (DKIM), [!DNL Domain-based Message Authentication], Reporting, and Conformance (DMARC).
* **High list quality**: Explicit opt-in, valid email acquisition methods, and engagement policies.
* **Consistent sending cadence and minimization of volume fluctuations**.
* **High IP and domain reputation**.

### Step 2: Email inbox placement

ISPs have unique, complex, and ever-changing algorithms to determine whether your email is placed in the inbox, the junk, or spam folder.

Here are some important factors for inbox placement:

* Delivered email
* High engagement
* Low complaints (less than 0.1 percent overall)
* Consistent volume
* Low spam traps
* Low hard bounce rate
* Lack of blocklist issues

### Step 3: Email engagement — opens

Here are some important factors for open rate:

* Email delivered and landed in the inbox
* Brand recognition
* Compelling subject line and preheaders
* Personalization
* Frequency
* Relevance or value of content

### Step 4: Email engagement — clicks

Here are some important factors for click rate:

* Email delivered, landed in the inbox, and opened
* Strong CTA
  * This is the primary action you want to achieve from your audience. Normally, it’s a click on a URL. Make sure it’s clear and easy for the user to find.
* Relevance or value of content

### Step 5: Conversion

Here are some important factors for conversion:

* All the above
* Transition from email via a working URL to a landing page or sales page
* Landing page experience
* Brand recognition, perception, and loyalty

### Potential impact on revenue

Conversion is key, but what’s the alternative? Your deliverability strategy can strengthen or wreak havoc on email marketing program nirvana. The following chart illustrates the potential loss in revenue that a weak deliverability policy can have on your marketing program. As demonstrated, for a business with a 2 percent conversion rate and average purchase of $100, every 10 percent reduction in inbox placement equals an almost $20,000 loss in revenue. Keep in mind that these numbers are unique for every sender.

| Sent | Percent   | Delivered | Percent  | Inbox | Number not in inbox | Conversion rate | Number of lost  | Average  | Lost      |
|------|-----------|-----------|----------|-------|---------------------|-----------------|-----------------|----------|-----------|
|      | delivered |           | inbox    |       |                     |                 | Conversions     | purchase | revenue   |
| 100K | 99%       | 99K       | 100%     | 99K   | -                   | 2%              | 0               | $100     | $ -       |
| 100K | 99%       | 99K       | 90%      | 89.1K | 9,900               | 2%              | 198             | $100     | $19,800   |
| 100K | 99%       | 99K       | 80%      | 79.2K | 19,800              | 2%              | 396             | $100     | $39,600   |
| 100K | 99%       | 99K       | 70%      | 69.3K | 29,700              | 2%              | 594             | $100     | $59,400   |
| 100K | 99%       | 99K       | 60%      | 59.4K | 39,600              | 2%              | 792             | $100     | $79,200   |
| 100K | 99%       | 99K       | 50%      | 49.5K | 49,500              | 2%              | 990             | $100     | $99,000   |
| 100K | 99%       | 99K       | 40%      | 39.6K | 59,400              | 2%              | 1188            | $100     | $118,800  |
| 100K | 99%       | 99K       | 30%      | 29.7K | 69,300              | 2%              | 1386            | $100     | $138,600  |
| 100K | 99%       | 99K       | 20%      | 19.8K | 79,200              | 2%              | 1584            | $100     | $158,400  |
