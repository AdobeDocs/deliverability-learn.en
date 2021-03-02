---
title: Duplicates
description:  Learn how to identify and limit duplicates to improve your deliverability when managing your platform.
feature: Deliverability
kt: 
thumbnail: 
doc-type: article
activity: understand
team: ACS
---

# Duplicates {#duplicates}

Having duplicate email addresses can have multiple consequences:

* The same message being sent more than once. Even if Adobe performs a deduplication procedure by default before sending, there is nothing to stop the same message being sent by different actions having the same content when a target is split.
* Unsubscription requests not honored. If a recipient unsubscribes after receiving a message, their duplicate profile will still be eligible for future messages.

Besides this side-stepping of opt-in procedures, this situation will likely lead users to consider the messages as spam and to trigger a denylist procedure at the ISP.

You must be especially prudent when performing operations on the database:

* Imports must be meticulously configured, in particular when choosing the reconciliation key.
* Changed email addresses can also be a source of duplicates. In particular, two addresses with different domains may be routed to the same mailbox, for example in the case of a company that has changed name and has maintained the former domain for a certain period of time: joe.doe@amce-co.com and joe.doe@acme-rebranded.com.
* Automatic imports, whether they be of lists or from other databases are elements to be taken into account when managing profiles. What happens when you delete or move a profile in another partition? It might be recreated in the initial partition by an automatic import, for example, when a purchase order is placed.
* Storing profiles in different folders can be implemented using views rather than partitions. In this way, you are sure that the profiles are in the same physical partition while still enabling the adequate rights to be displayed and managed.

There are, all the same, cases in which duplicates between the different partitions are normal. For example, when sending for third-parties or different company entities, it is logical for the same person to be a recipient for different reasons. It is, however, rarely normal to find duplicates within the same partition.