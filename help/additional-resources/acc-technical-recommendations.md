---
title: Campaign Classic - Technical recommendations
description: Discover techniques, configurations, and tools that you can use to improve your deliverability rate with Adobe Campaign Classic.
topics: Deliverability 
doc-type: article
activity: understand
team: ACS
exl-id: 39ed3773-18bf-4653-93b6-ffc64546406b
---
# Campaign Classic - Technical recommendations {#technical-recommendations}

Several techniques, configurations, and tools that you can use to improve your deliverability rate when using Adobe Campaign Classic are listed below.

## Configuration {#configuration}

### Reverse DNS {#reverse-dns}

Adobe Campaign checks whether a reverse DNS is given for an IP address and that this correctly points back to the IP.

An important point in the network configuration is making sure a correct reverse DNS is defined for each of the IP addresses for outgoing messages. This means that for a given IP address, there is a reverse DNS record (PTR record) with a matching DNS (A record) looping back to the initial IP address.

The domain choice for a reverse DNS has an impact when dealing with certain ISPs. AOL, in particular, only accepts feedback loops with an address in the same domain as the reverse DNS (see [Feedback loop](#feedback-loop)).

>[!NOTE]
>
>You can use [this external tool](https://mxtoolbox.com/SuperTool.aspx) to verify the configuration of a domain.

### MX rules {#mx-rules}

MX rules (Mail eXchanger) are the rules that manage communication between a sending server and a receiving server.

More precisely, they are used to control the speed at which the Adobe Campaign MTA (Message Transfer Agent) sends emails to each individual email domain or ISP (for example, hotmail.com, comcast.net). These rules are typically based on limits published by the ISPs (for example, do not include more than 20 messages per each SMTP connection).

>[!NOTE]
>
>For more on MX management in Adobe Campaign Classic, refer to [this section](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#mx-configuration).

### TLS {#tls}

TLS (Transport Layer Security) is an encryption protocol that can be used to secure the connection between two email servers and protect the content of an email from being read by anyone other than the intended recipients.

### Sender's domain {#sender-domain}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

### SPF record {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the two IP addresses, 12.34.56.78 and 12.34.56.79, as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).

>[!NOTE]
>
>Learn more on SPF in [this section](/help/additional-resources/authentication.md#spf).

## Authentication

>[!NOTE]
>
>Learn more on the different forms of email authentication in [this section](/help/additional-resources/authentication.md).

### DKIM {#dkim-acc}

>[!NOTE]
>
>For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-with-enhanced-mta.html#sending-messages), DKIM email authentication signing is done by the Enhanced MTA for all messages with all domains.

Using [DKIM](/help/additional-resources/authentication.md#dkim) with Adobe Campaign Classic requires the following prerequisite:

**Adobe Campaign option declaration**: in Adobe Campaign, the DKIM private key is based on a DKIM selector and a domain. It is not currently possible to create multiple private keys for the same domain/sub-domain with different selectors. It is not possible to define which selector domain/sub-domain must be used for the authentication in neither the platform or the email. The platform will alternatively select one of the private keys, which means the authentication has a high chance of failing.

* If you have configured DomainKeys for your Adobe Campaign instance, you just need to select **dkim** in the [Domain management rules](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#email-management-rules). If not, follow the same configuration steps (private/public key) as for DomainKeys (which replaced DKIM).
* It is not necessary to enable both DomainKeys and DKIM for the same domain as DKIM is an improved version of DomainKeys.
* The following domains currently validate DKIM: AOL, Gmail.

## Feedback loop {#feedback-loop-acc}

A feedback loop works by declaring at the ISP level a given email address for a range of IP addresses used for sending messages. The ISP will send to this mailbox, in a similar way as what is done for bounce messages, those messages that are reported by recipients as spam. The platform should be configured to block future deliveries to users who have complained. It is important to no longer contact them even if they did not use the proper opt-out link. It is based on these complaints that an ISP will add an IP address to its denylist. Depending on the ISP, a complaint rate of around 1% will result in blocking an IP address.

A standard is currently being drawn up to define the format of feedback loop messages: the [Abuse Feedback Reporting Format (ARF)](https://tools.ietf.org/html/rfc6650).

Implementing a feedback loop for an instance requires:

* A mailbox dedicated to the instance, which may be the bounce mailbox
* IP sending addresses dedicated to the instance

Implementing a simple feedback loop in Adobe Campaign uses the bounce message functionality. The feedback loop mailbox is used as a bounce mailbox and a rule is defined to detect these messages. The email addresses of the recipients who reported the message as spam will be added to the quarantine list.

* Create or modify a bounce mail rule, **Feedback_loop**, in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** with the reason **Refused** and the type **Hard**.
* If a mailbox has been defined specially for the feedback loop, define the parameters to access it by creating a new external Bounce Mails account in **[!UICONTROL Administration > Platform > External accounts]**.

The mechanism is immediately operational to process complaint notifications. To make sure this rule is working correctly, you can temporarily deactivate the accounts so that they do not collect these messages, then check the contents of the feedback loop mailbox manually. On the server, execute the following commands:

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

If you are forced to use one single feedback loop address for multiple instances, you must:

* Replicate the messages received on as many mailboxes as there are instances,
* Have each mailbox picked up by one single instance,
* Configure the instances so that they only process the messages that concern them: the instance information is included in the Message-ID header of messages sent by Adobe Campaign and is therefore located also in the feedback loop messages. Simply specify the **checkInstanceName** parameter in the instance configuration file (by default, the instance is not verified and this may lead certain address to be quarantined incorrectly):

  ```
  <serverConf>
    <inMail checkInstanceName="true"/>
  </serverConf>
  ```

Adobe Campaign's Deliverability service manages your subscription to feedback loop services for the following ISPs: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## List-Unsubscribe {#list-unsubscribe}

### About List-Unsubscribe {#about-list-unsubscribe}

Adding an SMTP header called **List-Unsubscribe** is mandatory to ensure optimal deliverability management.Starting on June 1, 2024, Yahoo and Gmail will be requiring senders to comply with One-Click List-Unsubscribe. To understand how to configure One-Click List-Unsubscribe please see below.


This header can be used as an alternative to the "Report as SPAM" icon. It will display as an unsubscribe link in the email interface.

Using this functionality helps to protect your reputation and feedback will be executed as an unsubscribe.

To use List-Unsubscribe, you must enter a command line similar to as follows:

```
List-Unsubscribe: <mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe>
```

>[!CAUTION]
>
>The example above is based on the recipient table. If database implementation is done from another table, make sure to reword the command line with the correct information.

The following command line can be used to create a dynamic **List-Unsubscribe**:

```
List-Unsubscribe: <mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%>
```

Gmail, Outlook.com, and Microsoft Outlook support this method and an unsubscribe button is available directly in their interface. This technique lowers complaint rates.

You can implement the **List-Unsubscribe** by either:

* Directly [adding the command line in the delivery template](#adding-a-command-line-in-a-delivery-template)
* [Creating a typology rule](#creating-a-typology-rule)

### Adding a command line in a delivery template {#adding-a-command-line-in-a-delivery-template}

The command line must be added in the additional section of the email's SMTP header.

This addition can be done in each email, or in existing delivery templates. You can also create a new delivery template that includes this functionality.

* List-Unsubscribe: <mailto:unsubscribe@domain.com> 
Clicking the unsubscribe link opens the user’s default email client. This typology rule must be added in a typology used for creating email.

* List-Unsubscribe: <https://domain.com/unsubscribe.jsp> 
Clicking the unsubscribe link redirects the user to your unsubscribe form.
![image](https://git.corp.adobe.com/storage/user/38257/files/3b46450f-2502-48ed-87b9-f537e1850963)


### Creating a typology rule {#creating-a-typology-rule}

The rule must contain the script that generates the command line and it must be included in the email header.

>[!NOTE]
>
>We recommend creating a typology rule: the List-Unsubscribe functionality will be automatically added in each email.

>[!NOTE]
>
>Learn how to create typology rules in Adobe Campaign Classic in [this section](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html#typology-rules).

### One-Click List Unsubscribe

Starting on June 1, 2024, Yahoo and Gmail will be requiring senders to comply with One-Click List-Unsubscribe. To comply with the One-Click List-Unsubscribe requirement senders must: 
 
* Add in a “List-Unsubscribe-Post: List-Unsubscribe=One-Click” 
* Include a URI unsubscribe Link 
* Support reception of the HTTP POST response from the receiver, which Adobe Campaign supports. 
 
To configure One-Click List-Unsubscribe directly: 
 
* Add in the following “Unsubscribe recipients no-click” web application  
* Go to Resources -> Online -> Web Applications 
* Upload the "Unsubscribe recipients no-click" XML 
* Configure List-Unsubscribe and List-Unsubscribe-Post 
* Go to the SMTP section of the Delivery Properties. 
* Under Additional SMTP Headers, enter in the command lines (Each header should be on a separate line): 
 
List-Unsubscribe-Post: List-Unsubscribe=One-Click 
List-Unsubscribe: <https://domain.com/webApp/unsubNoClick?id=<%= recipient.cryptidcamp %>>, <mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%> 
 
The above example will enable One-Click List-Unsubscribe for ISPs who support One-Click, while ensuring that receivers who do not support URL list-unsubscribe can still request a unsubscribe via email. 
 
Click here to see how to configure One-Click List-Unsubscribe via Typology Rule.

## Email optimization {#email-optimization}

### SMTP {#smtp}

SMTP (Simple mail transfer protocol) is an Internet standard for email transmission.

The SMTP errors that aren't checked by a rule are listed in the **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** folder. These error messages are by default interpreted as unreachable soft errors.

The most common errors must be identified and a corresponding rule added in **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** if you wish to correctly qualify the feedback from the SMTP servers. Without this, the platform will perform unnecessary retries (case of unknown users) or wrongly place certain recipients in quarantine after a given number of tests.

### Dedicated IPs {#dedicated-ips}

Adobe provides a dedicated IP strategy for each customer with a ramp-up IP in order to build a reputation and optimize delivery performance.
