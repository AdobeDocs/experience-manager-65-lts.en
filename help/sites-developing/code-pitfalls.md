---
title: Code pitfalls
description: Common coding pitfalls to avoid when developing for AEM
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 95656312-2648-455e-80fb-3e03bf1cd633
---
# Code pitfalls{#code-pitfalls}

## Avoid Sling Bindings in Java code {#avoid-sling-bindings-in-java-code}

Sling Bindings are an inappropriate way to get access to a service in 90% of cases. Instead, you should use *@Reference* or *@Inject* annotations.

## Avoid Thread.interrupt in Java code {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* is dangerous because it can close files, including Lucene files and persistent cache files, when called at the wrong time.

## Avoid mixing Java synchronization with ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

This can lead to a race condition in which the code will eventually deadlock.
