# Basic Platform Concepts
The central point of entry to the platform is the SAP BTP cockpit, where you can access your accounts and
applications and manage all activities associated with them.




### Global Account
A global account is the realization of a contract you or your company has made with SAP.
A global account is used to manage subaccounts, members, entitlements and quotas. You receive entitlements
and quotas to use platform resources per global account and then distribute the entitlements and quotas
to the subaccount for actual consumption. There are two types of commercial models for global accounts:
consumption-based model and subscription-based model.
Global accounts are region- and environment-independent. Within a global account, you manage all of your
subaccounts, which in turn are specific to one region.

Use SAP BTP cockpit to logon to our global account.

### Subaccount 
Subaccounts let you structure a global account according to your organization’s and project’s requirements
with regard to members, authorizations, and entitlements

Steps to create a sub account:
https://help.sap.com/docs/sap-hana-spatial-services/onboarding/creating-subaccount-on-sap-business-technology-platform-sap-btp

API: https://api.sap.com/api/APIAccountsService/resource/Subaccount_Operations

### Entitlements and Quotas
When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the
amount of memory that can be allocated to your applications.
An entitlement is your right to provision and consume a resource. In other words, entitlements are the service
plans that you're entitled to use.
A quota represents the numeric quantity of a service plan that you're entitled to consume in your global
account and its subaccounts
Entitlements and quotas are managed at the global account level, distributed to directories and subaccounts, and consumed by the subaccounts.

When you remove quotas or entitlements from a subaccount, they become available again at global account level and can be assigned to other subaccounts.

Steps to manage entitlements on BTP
https://developers.sap.com/tutorials/cp-trial-entitlements.html

https://help.sap.com/docs/sap-hana-spatial-services/onboarding/assign-subaccount-to-service

https://developers.sap.com/tutorials/cp-cf-entitlements-add.html

REST api: https://api.sap.com/api/APIEntitlementsService/resource/Manage_Assigned_Entitlements
Only available to manage the assigned entitlement. Did not find an api to create a new one.

### User management
Creating an user in BTP
https://help.sap.com/docs/btp/sap-business-technology-platform/create-users


### Role and Role Collections
Define a role collection:
https://help.sap.com/docs/btp/sap-business-technology-platform/define-role-collection
Add roles to a role collection;
https://help.sap.com/docs/btp/sap-business-technology-platform/add-roles-to-role-collection

Assigning role collection to user /user groups
https://help.sap.com/docs/btp/sap-business-technology-platform/assigning-role-collections-to-users-or-user-groups

Assign users to role collection
https://help.sap.com/docs/btp/sap-business-technology-platform/assign-users-to-role-collections

Assign user groups to a role
https://help.sap.com/docs/btp/sap-business-technology-platform/assign-user-groups-to-role-collections

### Destination in BTP

Destinations are predefined endpoints used in the Business Technology Platform (or BTP). Destinations allow you to securely store sensitive information used to connect to a system, such as client credentials, keys, or certificates in 
the BTP.
Creating destinations in BTP cockpit:

https://help.sap.com/docs/advanced-financial-closing/administration/how-to-create-destination-in-sap-btp-cockpit-s4hana-cloud

Managing Destinations:
To manage destinations for your application, choose a procedure that fits best your requirements.

There are various ways to manage destinations. Each method is characterized by different prerequisites and limitations. Before choosing a method, you should evaluate them and decide which one is the most appropriate for your particular scenario. The following link compares the available methods:
https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/managing-destinations

Our area of interest would be Destination Service REST API
The Destination service provides a REST API that you can use to read and manage resources like destinations, certificates and destination fragments on all available levels. This API is documented in the SAP Business Accelerator Hub published on SAP site.
Link: https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/overview

Please check the API reference provided in the below link 

https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource/

Calling the Destination Service REST API
https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/calling-destination-service-rest-api
For calling the REST api, destination service instance is needed inside your subaccount.

To access the Destination service REST API, you need an access token. To generate this token, you need credentials contained in a service key of the Destination service instance.

Information to extract from the service key
clientid: "<value_to_extract>"
The client ID that will be used for authentication in the next step.

clientsecret: "<value_to_extract>"
The client secret that will be used for authentication in the next step.

url: "<value_to_extract>"
The authentication endpoint from which you get an access token for the Destination service.

uri: "<value_to_extract>"
The URL of the Destination service.

Refer to the link https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/calling-destination-service-rest-api



### XSUAA 
### add authentication
Accessing Administration Using APIs of the SAP Authorization and Trust Management Service
https://help.sap.com/docs/btp/sap-business-technology-platform/accessing-administration-using-apis-of-sap-authorization-and-trust-management-service

https://api.sap.com/package/authtrustmgmnt/rest

 How to use REST API of XSUAA to programmatically manage security artifacts
https://community.sap.com/t5/technology-blogs-by-sap/sap-btp-security-how-to-use-rest-api-of-xsuaa-to-programmatically-manage/ba-p/13540720#samples

https://developers.sap.com/tutorials/btp-app-kyma-prepare-xsuaa.html
### Add authorisation(based on roles)
Users can be assigned to role collections via BTP cockpit.
Did not find any REST api to assign user to a specific role collection : https://api.sap.com/package/authtrustmgmnt/rest

### Service Manager
https://api.sap.com/api/APIServiceManager/overview
### Service instance 
https://api.sap.com/api/APIServiceManager/resource/Service_Instances
### Service binding
https://api.sap.com/api/APIServiceManager/resource/Service_Bindings


### Area of interest
We want to automate(one click) the process for creating destinations from inside CNS.
- Go to BTP Subaccount Destinations screen and Download Trust
- Create an IAM inbound OAuth2SAMLBearerAssertionFlow Link: https://github.wdf.sap.corp/pages/sapsalescloud/matterhorn-architecture/05-Microservices/IAM/iam-inbound-flows/
    - Please note: In the initial version, it would be possible to modify only the default SAP delivered OAuth configurations. The default configurations will be pre-delivered and it should be possible to only modify the 
      clientAppName and certificate as part of the customer setup.
    - Create an inbound configuration using the certificate that you downlaoded from btp cockpit(destinations). Response to the POST request will have the audience,tokenServiceUrl, clientId, clientAppName etc.
- In BTP cocokpit , under the Instance and Subscription option, add an instance of Destination Service.
- Once added, create a Service key and download the JSON. It will have the clientId/clientsecret/url/tenantid,verificationkey,sapname/uri etc.
- We need to make use of this clientid and client secret to generate the access token.
- Use the url that you get from the above service key and make a POST call to this:  <your_url>/oauth/token 
  with body in urlencoded form having the following:
  
    grant_type  -  client_credentials
  
    client_id   -  from service key json file
  
    client_secret - from service key json file

  
  On making the POST call, you will get the access token, scope and expiry time of the token.
- Use this access token to make the Destination service specific REST api calls like:

  GET https://destination-configuration.cfapps.us10.hana.ondemand.com/destination-configuration/v1/subaccountDestinations
  

  POST https://destination-configuration.cfapps.us10.hana.ondemand.com/destination-configuration/v1/subaccountDestinations


  Paylaod example, values to be filled from the response of the POST while creating the inbound configuration
  ```json
  {
    "Name": "NewDestination3",
    "Type": "HTTP",
    "URL": "abc.com",
    "Authentication": "OAuth2SAMLBearerAssertion",
    "tokenServiceURL": "https://demo.sapjam.com/api/v1/auth/token",
    "tokenServiceURLType": "Dedicated",
    "clientKey": "id",
    "audience": "somevalue",
    "nameQualifier": "somevalue",
    "apiKey": "apiKey",
    "PropertyName": "abc"}
  ```


Open Points:
https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/oauth-saml-bearer-assertion-authentication
- How to add key store location( KeyStoreLocation: Contains the name of the certificate configuration to be used for per-destination SAML assertion signing. This certificate will be used instead of the standard subaccount-wide signing key).
   /* will be marked as default */

- 


  




