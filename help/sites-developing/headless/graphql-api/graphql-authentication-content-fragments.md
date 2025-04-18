---
title: Authentication for Remote Adobe Experience Manager GraphQL Queries on Content Fragments
description: Understand the authentication required for Remote Adobe Experience Manager GraphQL queries to secure your headless content delivery.
feature: Content Fragments,GraphQL API
solution: Experience Manager, Experience Manager Sites
role: Developer
exl-id: 8891b13d-5d7d-4ac5-99ba-bde8bff58a6d
---
# Authentication for Remote Adobe Experience Manager GraphQL Queries on Content Fragments {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

A primary use case for The [Adobe Experience Manager (AEM) GraphQL API for Content Fragment Delivery](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) is to accept remote queries from third-party applications or services. These remote queries may require authenticated API access to secure headless content delivery.

>[!NOTE]
>
>For testing and development, you can also access the AEM GraphQL API directly using the [GraphiQL interface](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphiql-interface).

For authentication, the third-party service needs to authenticate, using the AEM account username and password.

<!-- 6.5.10.0 - does this content/page need to be migrated? -->

<!--
For authentication the third-party service needs to [retrieve an Access Token](#retrieving-access-token), that can then be [used in the GraphQL Request](#use-access-token-in-graphql-request).

## Retrieving an Access Token {#retrieving-access-token}

See [Generating Access Tokens for Server Side APIs](/help/sites-developing/generating-access-tokens-for-server-side-apis.md) for full details.

## Using the Access Token in a GraphQL Request {#use-access-token-in-graphql-request}

For a third-party service to connect with an AEM instance it needs to have an *Access Token*. The service must then add this token to the `Authorization` header on the POST request. 

For example, a GraphQL Authorization Header:

```xml
Authorization: Bearer <access_token>
```

## Permission Requirements {#permission-requirements}

All requests made using the access token will actually be made *by the user account that generated the token*. 

This means that you need to check that the account has the permissions required to run GraphQL queries. 

You can check this by using GraphiQL on the local instance.
-->
