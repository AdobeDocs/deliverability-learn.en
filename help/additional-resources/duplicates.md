---
title: Duplicates
description:  Learn how to identify and limit duplicates to improve deliverability.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: f89dbb38-a8d4-4294-b017-6fed72591593
---
# Duplicates {#duplicates}

Having duplicate email addresses can have multiple consequences:

* The same message being sent more than once. Even if Adobe performs a deduplication procedure by default before sending, there is nothing to stop the same message being sent by different actions having the same content when a target is split.
* Unsubscription requests not honored. If a recipient unsubscribes after receiving a message, their duplicate profile will still be eligible for future messages.

Besides this side-stepping of opt-in procedures, this situation will likely lead users to consider the messages as spam and to trigger a denylist procedure at the ISP.

You must be especially prudent when performing operations on the database:

* Imports must be meticulously configured, in particular when choosing the reconciliation key.
* Changed email addresses can also be a source of duplicates. In particular, two addresses with different domains may be routed to the same mailbox, for example if a company has changed name and has maintained the former domain for a certain time: joe.doe@amce-co.com and joe.doe@acme-rebranded.com.
* Automatic imports, whether of lists or from other databases, are elements to be considered when managing profiles. What happens when you delete or move a profile in another partition? It may be recreated in the initial partition by an automatic import, for example, when a purchase order is placed.
* Storing profiles in different folders can be implemented using views rather than partitions. In this way, you are sure that the profiles are in the same physical partition while still enabling the adequate rights to be displayed and managed.

There are, all the same, cases in which duplicates between the different partitions are normal. For example, when sending for third-parties or different company entities, it is logical for the same person to be a recipient for different reasons. It is, however, rarely normal to find duplicates within the same partition.

## Product specific resources

Deduplicating addresses protects your sending reputation and ensures good quarantine management. Learn more in the following product documentation sections:

**Adobe Campaign Classic**

* [Deduplication activity](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [Using the Deduplication activity’s Merge functionality](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html)

**Adobe Campaign Standard**

* [Deduplicating the data from an imported file](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)
