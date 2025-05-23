---
title: Importing and Exporting Data
description: Use the Form Data Integration service to import data into a PDF form and export data from a PDF form using the Java API and Web Service API.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: 2e8b73eb-7070-4b7b-b14b-bfcca6175afb
---
# Importing and Exporting Data {#importing-and-exporting-data} 

**Samples and examples in this document are only for AEM Forms on JEE environment.**

## About the Form Data Integration Service {#about-the-form-data-integration-service}

The Form Data Integration service can import data into a PDF form and export data from a PDF form. The import and export operations support two types of PDF forms:

* An Acrobat form (created in Acrobat) is a PDF document that contains form fields.
* An Adobe XML form (created in Designer) is a PDF document that conforms to the XML Adobe XML Forms Architecture (XFA).

Form data can exist in one of the following formats depending on the type of PDF form:

* An XFDF file, which is an XML version of the Acrobat form data format.
* An XDP file, which is an XML file that contains form field definitions. It may also contain form field data and an embedded PDF file. An XDP file generated by Designer can only be used if it carries an embedded base-64-encoded PDF document.

You can accomplish these tasks using the Form Data Integration service:

* Import data into PDF forms. For information, see [Importing Form Data](importing-exporting-data.md#importing-form-data).
* Export data from PDF forms. For information, see [Exporting Form Data](importing-exporting-data.md#exporting-form-data).

>[!NOTE]
>
>For more information about the Form Data Integration service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Importing Form Data {#importing-form-data}

You can import form data into interactive PDF forms by using the Form Data Integration service. An interactive PDF form is a PDF document that contains one or more fields for collecting information from a user or for displaying custom information. The Form Data Integration service does not support form calculations, validation, or scripting.

To import data into a form created in Designer, you must reference a valid XDP XML data source. Consider the following example mortgage application form.

![ie_ie_loanformdata](assets/ie_ie_loanformdata.png)

To import data values into this form, you must have a valid XDP XML data source that corresponds to the form. You cannot use an arbitrary XML data source to import data into a form using the Form Data Integration service. The difference between an arbitrary XML data source and an XDP XML data source is that an XDP data source conforms to the XML Forms Architecture (XFA). The following XML represents an XDP XML data source that corresponds to the example mortgage application form.

```xml
 <?xml version="1.0" encoding="UTF-8" ?>
 - <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
 - <xfa:data>
 - <data>
     - <Layer>
         <closeDate>1/26/2007</closeDate>
         <lastName>Johnson</lastName>
         <firstName>Jerry</firstName>
         <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
         <city>New York</city>
         <zipCode>00501</zipCode>
         <state>NY</state>
         <dateBirth>26/08/1973</dateBirth>
         <middleInitials>D</middleInitials>
         <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
         <phoneNumber>5555550000</phoneNumber>
     </Layer>
     - <Mortgage>
         <mortgageAmount>295000.00</mortgageAmount>
         <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
         <purchasePrice>300000</purchasePrice>
         <downPayment>5000</downPayment>
         <term>25</term>
         <interestRate>5.00</interestRate>
     </Mortgage>
 </data>
 </xfa:data>
 </xfa:datasets>
```

>[!NOTE]
>
>For more information about the Form Data Integration service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Summary of steps {#summary-of-steps}

To import form data into a PDF form, perform the following steps:

1. Include project files.
1. Create a Form Data Integration service client.
1. Reference a PDF form.
1. Reference an XML data source.
1. Import data into the PDF form.
1. Save the PDF form as a PDF file.

**Include project files**

Include necessary files into your development project. If you are creating a client application using Java, then include the necessary JAR files. If you are using web services, then make sure that you include the proxy files.

The following JAR files must be added to your project’s classpath:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (Required if AEM Forms is deployed on JBoss)
* jbossall-client.jar (Required if AEM Forms is deployed on JBoss)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Create a Form Data Integration service client**

Before you can programmatically import data into a PDF form Client API, you must create a Data Integration service client. When creating a service client, you define connection settings that are required to invoke a service. For information, see [Setting connection properties](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Reference a PDF form**

To import data into a PDF form, you must reference either an XML form created in Designer or an Acrobat form created in Acrobat.

**Reference an XML data source**

To import form data, you must reference a valid data source. To import data into an XFA XML form created in Designer, you must use an XDP XML data source. If you reference an Acrobat form, then you must use an XFDF data source. For each field that you want to import data into, a value must be specified. If an element in the XML data source does not correspond to a field in the form, then the element is ignored.

**Import data into the PDF form**

After you reference a PDF form and a valid XML data source, you can import the data into the PDF form.

**Save the PDF form as a PDF file**

After you import data into a form, you can save the form as a PDF file. Once saved as a PDF file, a user can open the form in Adobe Reader or Acrobat and see the form with the imported data.

**See also**

[Import form data using the Java API](importing-exporting-data.md#import-form-data-using-the-java-api)

[Import form data using the web service API](importing-exporting-data.md#import-form-data-using-the-web-service-api)

[Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Setting connection properties](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Form Data Integration Service API Quick Starts](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Exporting Form Data](importing-exporting-data.md#exporting-form-data)

### Import form data using the Java API {#import-form-data-using-the-java-api}

Import form data by using the Form Data Integration API (Java):

1. Include project files.

   Include client JAR files, such as adobe-formdataintegration-client.jar, in your Java project’s class path.

1. Create a Form Data Integration service client.

    * Create a `ServiceClientFactory` object that contains connection properties.
    * Create a `FormDataIntegrationClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Reference a PDF form.

    * Create a `java.io.FileInputStream` object by using its constructor. Pass a string value that specifies the location of the PDF form.
    * Create a `com.adobe.idp.Document` object that stores the PDF form by using the `com.adobe.idp.Document` constructor. Pass the `java.io.FileInputStream` object that contains the PDF form to the constructor.

1. Reference an XML data source.

    * Create a `java.io.FileInputStream` object by using its constructor and pass a string value that specifies the location of the XML file that contains data to import into the form.
    * Create a `com.adobe.idp.Document` object that stores form data by using the `com.adobe.idp.Document` constructor. Pass the `java.io.FileInputStream` object that contains form data to the constructor.

1. Import data into the PDF form.

   Import data into PDF form by invoking the `FormDataIntegrationClient` object’s `importData` method and passing the following values:

    * The `com.adobe.idp.Document` object that stores the PDF form.
    * The `com.adobe.idp.Document` object that stores form data.

   The `importData` method returns a `com.adobe.idp.Document` object that stores a PDF form that contains the data in the XML data source.

1. Save the PDF form as a PDF file.

    * Create a `java.io.File` object and ensure that the file extension is ".PDF".
    * Invoke the `Document` object’s `copyToFile` method to copy the contents of the `Document` object to the file (ensure that you use the `Document` object that was returned by the `importData` method).

**See also**

[Summary of steps](importing-exporting-data.md#summary-of-steps)

[Quick Start (SOAP mode): Importing form data using the Java API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Setting connection properties](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Import form data using the web service API {#import-form-data-using-the-web-service-api}

Import form data by using the Form Data Integration API (web service):

1. Include project files.

   Create a Microsoft .NET project that uses MTOM. Ensure that you use the following WSDL definition: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Replace `localhost` with the IP address of the server hosting AEM Forms.

1. Create a Form Data Integration service client.

    * Create a `FormDataIntegrationClient` object by using its default constructor.
    * Create a `FormDataIntegrationClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Pass a string value that specifies the WSDL to the AEM Forms service (for example, `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`.) You do not need to use the `lc_version` attribute. This attribute is used when you create a service reference. However, specify `?blob=mtom` to use MTOM.
    * Create a `System.ServiceModel.BasicHttpBinding` object by getting the value of the `FormDataIntegrationClient.Endpoint.Binding` field. Cast the return value to `BasicHttpBinding`.
    * Set the `System.ServiceModel.BasicHttpBinding` object’s `MessageEncoding` field to `WSMessageEncoding.Mtom`. This value ensures that MTOM is used.
    * Enable basic HTTP authentication by performing the following tasks:

        * Assign the AEM forms user name to the field `FormDataIntegrationClient.ClientCredentials.UserName.UserName`.
        * Assign the corresponding password value to the field `FormDataIntegrationClient.ClientCredentials.UserName.Password`.
        * Assign the constant value `HttpClientCredentialType.Basic` to the field `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
        * Assign the constant value `BasicHttpSecurityMode.TransportCredentialOnly` to the field `BasicHttpBindingSecurity.Security.Mode`.

1. Reference a PDF form.

    * Create a `BLOB` object by using its constructor. This `BLOB` object is used to store the PDF form.
    * Create a `System.IO.FileStream` object by invoking its constructor. Pass a string value that specifies the location of the PDF form and the mode in which to open the file.
    * Create a byte array that stores the content of the `System.IO.FileStream` object. You can determine the size of the byte array by getting the `System.IO.FileStream` object’s `Length` property.
    * Populate the byte array with stream data by invoking the `System.IO.FileStream` object’s `Read` method. Pass the byte array, the starting position, and the stream length to read.
    * Populate the `BLOB` object by assigning its `MTOM` field with the contents of the byte array.

1. Reference an XML data source.

    * Create a `BLOB` object by using its constructor. This `BLOB` object is used to store the data that is imported into the form.
    * Create a `System.IO.FileStream` object by invoking its constructor. Pass a string value that specifies the location of the XML file that contains data to import and the mode in which to open the file.
    * Create a byte array that stores the content of the `System.IO.FileStream` object. You can determine the size of the byte array by getting the `System.IO.FileStream` object’s `Length` property.
    * Populate the byte array with stream data by invoking the `System.IO.FileStream` object’s `Read` method. Pass the byte array, the starting position, and the stream length to read.
    * Populate the `BLOB` object by assigning its `MTOM` field with the contents of the byte array.

1. Import data into the PDF form.

   Import data into the PDF form by invoking the `FormDataIntegrationClient` object’s `importData` method and passing the following values:

    * The `BLOB` object that stores the PDF form.
    * The `BLOB` object that stores form data.

   The `importData` method returns a `BLOB` object that stores a PDF form that contains the data in the XML data source.

1. Save the PDF form as a PDF file.

    * Create a `System.IO.FileStream` object by invoking its constructor and passing a string value that represents the file location of the PDF file.
    * Create a byte array that stores the data content of the `BLOB` object that was returned by the `importData` method. Populate the byte array by getting the value of the `BLOB` object’s `MTOM` field.
    * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
    * Write the contents of the byte array to a PDF file by invoking the `System.IO.BinaryWriter` object’s `Write` method and passing the byte array.

**See also**

[Summary of steps](importing-exporting-data.md#summary-of-steps)

[Invoking AEM Forms using MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Exporting Form Data {#exporting-form-data}

You can export form data from an interactive PDF form by using the Form Data Integration service. The format of the data that is exported depends on the form type. If the form type is an Acrobat form created in Acrobat then the exported data is XFDF. If the form type is an XML form that was created in Designer, then the exported data is XDP.

>[!NOTE]
>
>For more information about the Form Data Integration service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Summary of steps {#summary_of_steps-1}

To export form data from a PDF form, perform the following steps:

1. Include project files
1. Create a Form Data Integration service client.
1. Reference a PDF form.
1. Export data from the PDF form.
1. Save the exported data as an XML file.

**Include project files**

Include necessary files into your development project. If you are creating a client application using Java, then include the necessary JAR files. If you are using web services, then make sure that you include the proxy files.

The following JAR files must be added to your project’s classpath:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (Required if AEM Forms is deployed on JBoss)
* jbossall-client.jar (Required if AEM Forms is deployed on JBoss)

**Create a Form Data Integration service client**

Before you can programmatically import data into a PDF formClient API, you must create a Data Integration service client. When creating a service client, you define connection settings that are required to invoke a service. For information, [Setting connection properties](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Reference a PDF form**

To export data from a PDF form, you must reference PDF form that was created in Designer or Acrobat and that contains form data. If you attempt to export data from an empty PDF form, you will get an empty XML schema.

**Export data from the PDF form**

After you reference a PDF form that contains form data, you can export the data from the form. The data is exported within an XML schema that is based on the form.

**Save the form data as an XML file**

After you export form data, you can save the data as an XML file. Once saved as an XML file, you can open the XML file within an XML viewer to view the form data.

**See also**

[Export form data using the Java API](importing-exporting-data.md#export-form-data-using-the-java-api)

[Export form data using the web service API](importing-exporting-data.md#export-form-data-using-the-web-service-api)

[Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Setting connection properties](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Form Data Integration Service API Quick Starts](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Importing Form Data](importing-exporting-data.md#importing-form-data)

### Export form data using the Java API {#export-form-data-using-the-java-api}

Export form data by using the Form Data Integration API (Java):

1. Include project files.

   Include client JAR files, such as adobe-formdataintegration-client.jar, in your Java project’s class path.

1. Create a Form Data Integration service client.

    * Create a `ServiceClientFactory` object that contains connection properties.
    * Create a `FormDataIntegrationClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Reference a PDF form.

    * Create a `java.io.FileInputStream` object by using its constructor and pass a string value that specifies the location of the PDF form that contains data to export.
    * Create a `com.adobe.idp.Document` object that stores the PDF form by using the `com.adobe.idp.Document` constructor. Pass the `java.io.FileInputStream` object that contains the PDF form to the constructor.

1. Export data from the PDF form.

   Export form data by invoking the `FormDataIntegrationClient` object’s `exportData` method and pass the `com.adobe.idp.Document` object that stores the PDF form. This method returns a `com.adobe.idp.Document` object that stores form data as an XML schema.

1. Save the PDF form as a PDF file.

    * Create a `java.io.File` object and ensure that the file extension is XML.
    * Invoke the `Document` object’s `copyToFile` method to copy the contents of the `Document` object to the file (ensure that you use the `Document` object that was returned by the `exportData` method).

**See also**

[Summary of steps](importing-exporting-data.md#summary-of-steps)

[Quick Start (SOAP mode): Exporting form data using the Java API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

[Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Setting connection properties](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Export form data using the web service API {#export-form-data-using-the-web-service-api}

Export form data by using the Form Data Integration API (web service):

1. Include project files.

   Create a Microsoft .NET project that uses MTOM. Ensure that you use the following WSDL definition: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

    * Replace `localhost` with the IP address of the server hosting AEM Forms.

1. Create a Form Data Integration service client.

    * Create a `FormDataIntegrationClient` object by using its default constructor.
    * Create a `FormDataIntegrationClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Pass a string value that specifies the WSDL to the AEM Forms service (for example, `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`.) You do not need to use the `lc_version` attribute. This attribute is used when you create a service reference. However, specify `?blob=mtom` to use MTOM.
    * Create a `System.ServiceModel.BasicHttpBinding` object by getting the value of the `FormDataIntegrationClient.Endpoint.Binding` field. Cast the return value to `BasicHttpBinding`.
    * Set the `System.ServiceModel.BasicHttpBinding` object’s `MessageEncoding` field to `WSMessageEncoding.Mtom`. This value ensures that MTOM is used.
    * Enable basic HTTP authentication by performing the following tasks:

        * Assign the AEM forms user name to the field `FormDataIntegrationClient.ClientCredentials.UserName.UserName`.
        * Assign the corresponding password value to the field `FormDataIntegrationClient.ClientCredentials.UserName.Password`.
        * Assign the constant value `HttpClientCredentialType.Basic` to the field `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
        * Assign the constant value `BasicHttpSecurityMode.TransportCredentialOnly` to the field `BasicHttpBindingSecurity.Security.Mode`.

1. Reference a PDF form.

    * Create a `BLOB` object by using its constructor. This `BLOB` object is used to store the PDF form from which data is exported.
    * Create a `System.IO.FileStream` object by invoking its constructor. Pass a string value that specifies the location of the PDF form and the mode in which to open the file.
    * Create a byte array that stores the content of the `System.IO.FileStream` object. You can determine the size of the byte array by getting the `System.IO.FileStream` object’s `Length` property.
    * Populate the byte array with stream data by invoking the `System.IO.FileStream` object’s `Read` method and passing the byte array, the starting position, and the stream length to read.
    * Populate the `BLOB` object by assigning its `MTOM` field with the contents of the byte array.

1. Export data from the PDF form.

   Import data into PDF form by invoking the `FormDataIntegrationClient` object’s `exportData` method and pass the `BLOB` object that stores the PDF form. This method returns a `BLOB` object that stores form data as an XML schema.

1. Save the PDF form as a PDF file.

    * Create a `System.IO.FileStream` object by invoking its constructor and passing a string value that represents the location of the XML file.
    * Create a byte array that stores the data content of the `BLOB` object that was returned by the `exportData` method. Populate the byte array by getting the value of the `BLOB` object’s `MTOM` field.
    * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
    * Write the contents of the byte array to an XML file by invoking the `System.IO.BinaryWriter` object’s `Write` method and passing the byte array.

**See also**

[Summary of steps](importing-exporting-data.md#summary-of-steps)

[Invoking AEM Forms using MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Invoking AEM Forms using SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
