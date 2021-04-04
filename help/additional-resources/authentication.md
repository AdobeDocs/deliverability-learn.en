---
title: Authentication
description:  Learn more on SPF, DKIM, and DMARC authentication methods.
feature: Additional resources
topics: Deliverability
kt: 
thumbnail: 
doc-type: article
activity: understand
team: ACS
exl-id: 03609139-b39b-4051-bcde-9ac7c5358b87
---
# Authentication

## SPF {#spf}

SPF (Sender Policy Framework) is an email authentication standard that allows the owner of a domain to specify which email servers are allowed to send email on behalf of that domain. This standard uses the domain in the email's "Return-Path" header (also referred to as the "Envelope From" address).

>[!NOTE]
>
>You can use [this external tool](https://www.kitterman.com/spf/validate.html) to verify an SPF record.

The SPF is a technique that, to a certain extent, enables you to make sure that the domain name used in an email is not forged. When a message is a received from a domain, the DNS server of the domain is queried. The response is a short record (the SPF record) that details which servers are authorized to send emails from this domain. If we assume that only the owner of the domain has the means to change this record, we can consider that this technique does not allow the sender address to be forged, at least not the part from the right of the "@".

In the final [RFC 4408 specification](https://www.rfc-editor.org/info/rfc4408), two elements of the message are used to determine the domain considered as the sender: the domain specified by the SMTP "HELO" (or "EHLO") command and the domain specified by the address of the "Return-Path" (or "MAIL FROM") header, which is also the bounce address. Different considerations make it possible to take into account one of these values only; we recommend making sure that both sources specify the same domain.

Checking the SPF provides an evaluation of the validity of the sender's domain:

* **None**: No evaluation could be performed.
* **Neutral**: The domain queried does not enable evaluation.
* **Pass**: The domain is considered authentic.
* **Fail**: The domain is forged and the message should be rejected.
* **SoftFail**: The domain is probably forged but the message should not be rejected solely based on this result.
* **TempError**: A temporary error stopped the evaluation. The message can be rejected.
* **PermError**: The SPF records of the domain are invalid.

It is worth noting that records made at the level of the DNS servers can take up to 48 hours to be taken into account. This delay depends on how often the DNS caches of the receiving servers are refreshed.

## DKIM {#dkim}

DKIM (DomainKeys Identified Mail) authentication is a successor to SPF. It uses public-key cryptography that allows the receiving email server to verify that a message was in fact sent by the person or entity it claims it was sent by, and whether the message content was altered in between the time it was originally sent (and DKIM "signed") and the time it was received. This standard typically uses the domain in the "From" or "Sender" header.

DKIM comes from a combination of the DomainKeys, Yahoo! and Cisco Identified Internet Mail authentication principles and is used to check the authenticity of the sender domain and guarantee the integrity of the message.

DKIM replaced **DomainKeys** authentication.

Using DKIM requires some prerequisites:

* **Security**: Encryption is a key element of the DKIM. To ensure the security level of the DKIM, 1024b is the best practice recommended encryption size. Lower DKIM keys are not considered as valid by the majority of access providers.
* **Reputation**: Reputation is based on the IP and/or the domain, but the less transparent DKIM selector is also a key element to be taken into account. Choosing the selector is important: avoid keeping the “default” one which could be used by anyone and therefore has a weak reputation. You must implement a different selector for **retention vs. acquisition communications** and for authentication.

Learn more on DKIM prerequisite when using Campaign Classic in [this section](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) is the most recent form of email authentication, and it relies on both SPF and DKIM authentication to determine whether an email passes or fails. DMARC is unique and powerful in two important ways:

* Conformance – it allows the sender to instruct the ISPs on what to do with any message that fails to authenticate (for example: do not accept it).
* Reporting – it provides the sender with a detailed report showing all messages that failed DMARC authentication, along with the "From" domain and IP address used for each. This allows a company to identify legitimate email that's failing authentication and needs some type of "fix" (for example, adding IP addresses to their SPF record), as well as the sources and prevalence of phishing attempts on their email domains.

>[!NOTE]
>
>DMARC can leverage the reports generated by [250ok](https://250ok.com/).
