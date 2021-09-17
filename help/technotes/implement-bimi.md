---
title: Implement Gmail's Brand Indicators for Message Identification (BIMI)
description: Learn how to implement BIMI
topics: Deliverability
hide: yes
hidefromtoc: yes
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
---
# Implement Gmail's [!DNL Brand Indicators for Message Identification] (BIMI)

Gmail recently announced that they would be [rolling out general support of BIMI](https://cloud.google.com/blog/products/identity-security/bringing-bimi-to-gmail-in-google-workspace). There are a number of items you will have to deal with before you can take advantage of this though including: Verified Mark Certificates, Trademarked Logos, Properly formatted Logos, DMARC setup, and finally publishing a BIMI record to your DNS. We will review all of these steps in this article.

[!DNL Brand Indicators for Message Identification] (BIMI) is an industry standard that allows an approved logo to appear next to a sender’s email in participating platforms. Not only is this eye catching possibly boosting engagement, it also helps confirm the authenticity of the sender reducing the risk of phishing and other spammy tactics.  

## Verified Mark Certificate 

One of the key components of Gmail’s BIMI program is the requirement that senders have a Verified Mark Certificate (VMC) issued by a valid Certificate Authority. Currently these VMCs are available only from Entrust and DigiCert, but that list of providers is likely to grow following Gmail’s announcement. 

VMCs will be similar to SSL certificates in some ways. You will need one VMC for each logo you want to have displayed, so if you have a lot of brands you should plan on needing multiple VMCs. Each VMC can be valid across multiple domains though if you get a Multi-SAN VMC. So if you want one logo to appear across multiple sending domains, you only need one VMC.  

## Logo Trademark 

Before you can get your VMC, there is another key step that must be completed. To get a VMC the logo you want to have displayed must be registered with one of 8 approved global trademark and patent offices.  

* United States Patent and Trademark Office (USPTO)
* Canadian Intellectual Property Office
* European Union Intellectual Property Office
* UK Intellectual Property Office
* Deutsches Patent- und Markenamt 
* Japan Trademark Office
* Spanish Patent and Trademark Office O.A.
* IP Australia

If the logo you want displayed is not registered, or is not registered with one of these 8 organizations, then you will need to work with your legal team to address that before applying for the VMC.  

## Logo Image Format 

This would also be a good time to make sure that your logo will meet the BIMI logo requirements for format. It must be in SVG format and adhere to SVG Portable/Secure (SVG-P/S) profile. Guidance around how to do so can be found at the [BIMI Working Group](https://bimigroup.org/svg-conversion-tools-released).

## DMARC 

Once you have your Trademarked Logo properly formatted, and your Verified Mark Certificate, you will also need to make sure that DMARC is fully configured on any sending domain you want BIMI to work for. 

This includes making sure the P= is set to either Quarantine or Reject. If your DMARC uses P=None it will not qualify for BIMI. The P=None setting is highly recommended to make sure you know what mail is going out from a domain and that nothing would be accidentally blocked if you changed to either “Quarantine” or “Reject”, think of it as the testing and information gathering phase. You will need to move beyond that into enforcement though before BIMI becomes available to you.  

## DNS Entry 

With everything else finally lined up and ready to go, it is time to update the DNS entry with your BIMI. 

This is a simple entry that should look something like this: 

```
default._bimi.[domain] IN TXT “v=BIMI1; l=[SVG URL] 
```

You can get the details around that entry and even use a free BIMI checker at the [BIMI working group site](https://bimigroup.org/implementation-guide).


## Key Takeaways 

If you are an [!DNL Adobe Campaign] or Marketo client, Adobe can help you with creating the BIMI DNS update: contact Adobe Customer Care to request one. Adobe can also help with troubleshooting if BIMI is not working correctly for you.  

For help with Trademarks or Verified Mark Certificates, work with your legal team and an authorized VMC vendor.  

Getting BIMI setup for Gmail may not be a quick process, but it is one that can have significant benefits both from a Marketing and a Security perspective.
