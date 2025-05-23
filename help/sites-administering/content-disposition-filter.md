---
title: Content Disposition Filter
description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
exl-id: 997cb6f3-1ef8-409c-acea-157d5b27a6b2
---
# Content Disposition Filter {#content-disposition-filter}

Content disposition filter is a security feature against XSS attacks on SVG files.

Once installed, the filter blocks access to all assets. For example, you could not view a PDF online. This section describes how to configure the filter to your needs.

## Configure Content Disposition Filter {#configure-content-disposition-filter}

You can view the [Apache Sling Content Disposition Filter in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java).

The Content Disposition Filter options provide the following functionality:

* **Content Disposition Paths:** A list of paths where the filter is applied followed by a list of mime-types to exclude on that path. This path must be an absolute path and may contain a wildcard (`*`) at the end, to match every resource path with the given path prefix. For example: `/content/*:image/jpeg,image/svg+xml` applies the filter to every node in `/content?` except JPG and SVG images.

* **Excluded Resource Paths:** A list of excluded resources, each resource path must be given as absolute and fully qualified path. Prefix matching/wildcards are not supported.

* **Enable For All Resource Paths:** This flag controls whether to enable this filter for all paths, except for the excluded paths defined by Excluded Resource Paths. Setting this flag to 'true' leads to ignoring Content Disposition Paths. Independent of the configuration, only resource paths are covered which contain a property named `jcr:data` or `jcr:content/jcr:data`.
