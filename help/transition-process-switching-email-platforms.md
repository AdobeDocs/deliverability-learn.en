---
title: What do I need to know when switching email platforms
description: When moving email service providers (ESPs), it’s not possible to also transition your existing, established IP addresses. It is important that you follow best practices for developing a positive reputation when starting afresh. 
feature: Deliverability
topics: 
kt: 5259
doc-type: article
activity: understand
team: ACS
---

# Transition process: switching email platforms

When moving email service providers (ESPs), it is not possible to also transition your existing, established IP addresses. It is important that you follow best practices for developing a positive reputation when starting afresh. Because the new IP addresses you will be using do not yet have reputation, ISPs are unable to fully trust the mail coming from them and need to be cautious in what they allow to be delivered to their customers.

Establishing a positive reputation is a process. But once it’s established, small negative indicators will have less impact to you and your mail delivery.

![Transition process](assets/transition-process.png)

The amount of time to warm your IP addresses and domains may vary, but up to an eight-week benchmark is common for typical senders to establish a reputation at most Tier 1 ISPs (Gmail, Microsoft, Verizon/Yahoo/AOL, etc.).

In the next sections, we’ll investigate some key areas to focus on to onboard properly.

## Infrastructure

Successful deliverability depends on a strong foundation. Email infrastructure is a core element. A properly constructed email infrastructure includes multiple components — namely domain(s) and IP address(es). These components are like the machinery behind the emails you send and they’re oftentimes the anchor of sending reputation. Deliverability consultants ensure that these elements are set up properly during implementation, but due to the reputation element, it is important for you to have this basic understanding.

## Domain setup and strategy

Times have changed, and some ISPs (like Gmail and Yahoo) now incorporate domain reputation as an additional point when it comes to attaching email reputation to a sender. Your domain reputation is based on your sending domain instead of your IP address. This means that your brand takes precedence when it comes to ISP filtering decisions.

Part of the onboarding process for new senders on Adobe platforms include setting up your sending domains and ensuring that your infrastructure is established properly. You should work with an expert on what domains you plan to use in the long term. Here are some tips that shape a good domain strategy:

* Be as clear and reflective of the brand as possible with the domain you choose so that users don’t incorrectly identify the mail as spam. Some examples are newsletter.foo.com, receipts.foo.com, and so on.
* You shouldn’t use your parent or corporate domain as it could impact the delivery of mail from your organization to ISPs.
* Consider using a subdomain of your parent domain to legitimize your sending domain.
* Separate your subdomains for Transactional and Marketing message categories. This will help your email traffic flow on a more reliable basis as ISPs look for this sending method, which is a known email best practice and is highly recommended.

## IP strategy

It is important to form a well-structured IP strategy to help establish a positive reputation. The number of IPs and setup varies depending on your business model and marketing goals. Work with an expert to develop a clear strategy to start off right. Consider these things that are important to note:

* **Too many IPs** can trigger reputation issues as it is a common tactic of spammers to **snowshoe**, which is a tactic used by spammers where traffic is spread across many IPs to maximize the delivery of spam mail. Even though you’re not a spammer, you might look like one if you use too many IPs, especially if those IPs haven’t had any prior traffic.
* **Too few IPs** can cause throughput issues and potentially trigger reputation issues. Throughput varies by ISP. How much and how quickly an ISP is willing to accept is typically based on their infrastructure and sending reputation thresholds.
* Separating traffic for messaging types is key. It is important to, at a bare minimum, separate marketing and transactional mail on separate IP pools.
* Depending on your mail strategy, it may also be advisable to separate different products or marketing streams on different IP pools if your reputation is drastically different. Some marketers also segment by region. Separating the IP for traffic with a lower reputation will not fix the reputation issue, but it will prevent issues with your “good” reputation email deliveries. After all, you don’t want to sacrifice your good audience for a riskier one.

## Feedback loops

Behind the scenes, Adobe platforms are processing data regarding bounces, complaints, unsubscribes, and more. The setup of these feedback loops is an important aspect to deliverability. Complaints can damage a reputation, so you should email addresses that register complaints from your target audience. It’s important to note that Gmail doesn’t provide this data back. List unsubscribe headers and engagement filtering are especially important for Gmail subscribers, who now comprise the majority of subscriber databases.

## Product specific resources

Campaign Standard

* [Control Panel: Full subdomain delegation] (https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)
* 

Campaign Classic

* [Control Panel: Full subdomain delegation] (https://experienceleague.corp.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)

