---
title: AEM Forms Blocks Valid HTTP Requests
description: AEM Forms XSS validation checks can block valid HTTP requests for customers using custom components. Learn how to identify the issue and temporarily relax the validation checks.
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin,Developer
exl-id: 10a02e57-7ff8-42d8-b31e-f714c0dd8338
---
# AEM Forms Blocks Valid HTTP Requests {#aem-forms-blocks-valid-http-requests}

## Issue {#issue}

AEM Forms includes security checks to prevent cross-site scripting (XSS) attacks. These checks can block some valid HTTP requests for customers who use custom components in AEM Forms. When a request is blocked, the following message appears in the server logs:

```text
Got Exception while Validating XSS: HTTP parameter name: params[browserLocale]: Invalid input. Please conform to regex ^[a-zA-Z0-9_]{1,32}$ with a maximum length of 2000: org.owasp.esapi.errors.ValidationException: HTTP parameter name: params[browserLocale]: Invalid input. Please conform to regex ^[a-zA-Z0-9_]{1,32}$ with a maximum length of 2000.
```

>[!NOTE]
>
>For a POST request, the default value for the parameter is **1048576**. For a GET request, the default value for the parameter is **2000**. To modify the parameter value for a POST request, pass the `com.adobe.idp.dsc.provider.rest.httpParamMaxSize` argument during server startup.

## Cause {#cause}

The XSS validation regex is stricter than the format of the parameter value sent by the custom component, so AEM Forms rejects the request.

## Resolution {#resolution}

>[!CAUTION]
>
>Removing the security checks makes the system vulnerable to cross-site scripting (XSS) attacks. Remove the security checks only as a temporary solution.

To temporarily remove the security checks and allow all HTTP requests:

1. Stop the AEM Forms server.

1. Create a backup of the `[AEM-Forms-Installation-Directory]/configurationManager/export/adobe-livecycle-<application_server_name>.ear` file.

1. Extract the `esapi-helper-2.x.x.jar` file from the `adobe-livecycle-<server_name>.ear` file. The location of the `esapi-helper-2.x.x.jar` file differs for each application server:

   | Application Server | Location of the esapi-helper-2.x.x.jar file |
   | --- | --- |
   | JBoss | `adobe-livecycle-jboss.ear/lib` |
   | Oracle WebLogic | `adobe-livecycle-weblogic.ear/APP-INF/lib` |
   | IBM WebSphere | `adobe-livecycle-websphere.ear/` |

1. Open the `[extracted esapi-helper-2.x.x.jar]/esapi/validation.properties` and `[extracted esapi-helper-2.x.x.jar]/esapi/ESAPI.properties` files for editing.

1. Set the value of the following properties to `^[\\s\\S]*$`. For example, `Validator.HTTPParameterName=^[\\s\\S]*$`. Save and close the files.

   * `Validator.HTTPQueryString`
   * `Validator.PMCallParameterName`
   * `Validator.PMCallParameterValue`
   * `Validator.HTTPParameterName`
   * `Validator.HTTPParameterValue`
   * `Validator.xssSafeString`

1. Package the updated `esapi-helper-2.x.x.jar` in `adobe-livecycle-<application_server_name>.ear`. Deploy the updated `adobe-livecycle-<application_server_name>.ear` to the application server.

1. Start the AEM Forms server.

## Reference {#references}

* [Mitigating Server-Side Request Forgery (SSRF) Vulnerabilities for AEM Forms on JEE 6.5 LTS SP2](/help/forms/troubleshooting/mitigating-server-side-request-forgery-vulnerabilities-for-aem-forms-on-jee-65-lts-sp2.md)
