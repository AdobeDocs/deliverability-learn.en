---
title: Implement Gmail's Brand Indicators for Message Identification (BIMI)
description: Learn how to implement BIMI
topics: Deliverability
role: Admin
level: Beginner
jira: KT-14079
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
---
# Implement [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI) is an industry standard that allows an approved logo to appear next to a sender's email in participating platforms.

With this standard, a brand can determine a logo which should be displayed in mailbox providers' inboxes. Once published in a so-called BIMI DNS (Domain Name System) record, a mailbox provider might pick this logo up and display it in the inbox if certain criteria are met.

Different providers do different implementations, but the benefits are clear: standing out in the inbox, building trust and being in control of what is being shown.

BIMI does not directly improve deliverability or your reputation. It can help build more trust with your recipients and therefore drive more engagement though.

## How does it look like?

You can find some examples of implementations from different providers and more details on whixh providers do display the logo on the [BIMI Group's page](https://bimigroup.org/where-is-my-bimi-logo-displayed/){target="_blank"}.

## Who is the BIMI Group?

The BIMI group is a working group developing BIMI as it not only covers the logo but also the technical, legal and compliance requirements.

The BIMI Group consists of several stakeholders from different areas of the industry: Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail and Validity.

## Who is supporting BIMI?

The mailbox providers' list supporting BIMI is growing steadily. An up-to-date list can be found [here](https://bimigroup.org/bimi-infographic/){target="_blank"} for both supporting providers as well as providers considering BIMI.

As of April 2023, the list includes Gmail, Yahoo, La Poste, Fastmail, Onet.pl and Zone, Proofpoint as an anti-spam appliance and Apple Mail (from iOS 16 onwards).

The most prominent names on that list are obviously Yahoo, Gmail and one recent adopter: Apple with iOS 16. Apple takes a special role in the mix as they are not a mailbox provider, but they did add BIMI support to their native mail app. Mail being compliant with BIMI will be displayed as "digitally certified email" which boosts the trust in the brand.

## Implementation

Implementing BIMI does come in several steps:

1. DMARC (Domain based Message Authentication, Reporting and Conformance) implementation on enforcement level for both the sending domain and its organizational domain - [Learn more](#dmarc)

1. Creation of your brand logo in the SVG TinyPS format - [Learn more](#create-brand-logo)

1. Signing up for a Verified Mark Certificate (only needed for some providers) - [Learn more](#vmc)

1. Publish a BIMI DNS record with the logo and the certificate - [Learn more](#publish-bimi-record)

1. Having a good reputation - [Learn more](#good-reputation)

>[!NOTE]
>
>Note that all steps need to be checked off.


### DMARC {#dmarc}

DMARC is a standard which allows the brand to decide what a mailbox provider should do with an email which fails [authentication](../additional-resources/authentication.md). The so-called policies range from "none" over "quarantine" (Spam folder placement) to "reject" (outright block the mail). Only the latter two policies are called "enforcement" and qualify for BIMI. Mail sent by Adobe is passing authentication, as SPF (Sender Policy Framework) and DKIM (Domain Keys Identified Mail) are set up per default. Adobe is setting up DMARC on your sending domain on request.

In addition to DMARC on the sending domain, DMARC also needs to be employed on enforcement level for the organizational domain (if the sending domain is news.example.com, example.com is the organizational domain).

### Creation of your brand logo {#create-brand-logo}

The logo creation needs to follow the requirements to 100%. Please always refer to the [BIMI Group's guidelines](https://bimigroup.org/creating-bimi-svg-logo-files/){target="_blank"}.

The logo needs to be stored in a secure location (HTTPS), in case a content delivery network (CDN) is used any protection which prevents Mailbox Providers from getting the logo (e.g. Bot Protection) needs to be disabled.

Besides the technical requirements, there are some practical recommendations like having a square logo, having a solid color as background and others. These recommendations are for best visualization. Some providers have their own requirements which are additional to the ones by the BIMI working group. [Gmail](https://support.google.com/a/answer/10911027?sjid=903725605955621707-EU){target="_blank"} for example requires the logo to be at least 96 x 96 pixels.
Please note that non-compliance can lead to the logo not being displayed. 

### Verified Mark Certificate (VMC) {#vmc}

A Verified Mark Certificate (VMC) is only needed for some mailbox providers like Gmail and Apple, and therefore is optional. We do recommend getting a VMC though to really leverage BIMI.

A Verified Mark Certificate is a legal validation that the brand can use the logo. A certification authority will check this through the trademark office where the brand logo is registered. This process involves several legal validations and checks, and can take some time. Currently two CAs (certificate authorities) are issuing VMCs: Digicert and Entrust. The first set of trademark offices are US, Canada, EU, UK, Germany, Japan, Australia, and Spain.

As a general rule, you will need one VMC per logo. Having a VMC for your organizational domain will cover subdomains, and with an added feature even different domains. In case you have different logos, more than one VMC is needed. The Certification Authority or partner you choose to work with will help you set this up.

>[!NOTE]
>
>Note that VMCs have a yearly fee.

### Publishing the BIMI record {#publish-bimi-record}

Once the other steps are done, the BIMI DNS record can be published. The record looks like this:

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

"PEM URL" is the file location of the Verified Mark Certificate.

For your sending domain, this needs to be done by Adobe.

### Good reputation {#good-reputation}

Trust is key for BIMI. The user is trusting their mailbox provider to only show the logo for legitimate senders, so the mailbox provider needs to trust the brand, and this is being done by your sender reputation. If you have a high reputation, all is good, but if you are not, the logo won't be displayed. Unfortunately, there is no information or metric we can look at to figure out if the reputation is high enough.

Even going through the effort and expenses for a VMC doesn't take away this part. If the mailbox provider doesn't trust the brand, the logo won't be displayed.

## Tips and Tricks

* The BIMI Group offers a handy validation tool for BIMI. If you want to double check if everything is set up and ready, or just want to see if the logo is compliant, go to [this link](https://bimigroup.org/bimi-generator/){target="_blank"}. For the latter just click **[!UICONTROL Generate BIMI]** and enter a placeholder domain but the correct logo URL. The inspector will tell you if the logo is compliant.

* You can safely start off without a VMC, there is no harm on your reputation if your BIMI record doesn't include a VMC URL, but the logo can already be shown in Yahoo.

* Implementing DMARC on an organizational level is a large undertaking. Some companies are specialized to help brands achieve a full DMARC adoption.

* An extensive list of frequently asked questions is published [here](https://bimigroup.org/faqs-for-senders-esps/){target="_blank"}.
