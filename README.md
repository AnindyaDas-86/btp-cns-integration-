# Basic Platform Concepts
The central point of entry to the platform is the SAP BTP cockpit, where you can access your accounts and
applications and manage all activities associated with them.




### Global Account
A global account is the realization of a contract you or your company has made with SAP.
A global account is used to manage subaccounts, members, entitlements and quotas. You receive entitlements
and quotas to use platform resources per global account and then distribute the entitlements and quotas
to the subaccount for actual consumption. There are two types of commercial models for global accounts:
consumption-based model and subscription-based model. See Commercial Models [page 65] .
Global accounts are region- and environment-independent. Within a global account, you manage all of your
subaccounts, which in turn are specific to one region.

Use SAP BTP cockpit to logon to our global account.

### Subaccount 
Subaccounts let you structure a global account according to your organization’s and project’s requirements
with regard to members, authorizations, and entitlements

Steps to create a sub account:
https://help.sap.com/docs/sap-hana-spatial-services/onboarding/creating-subaccount-on-sap-business-technology-platform-sap-btp

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


### Destination in BTP
### XSUAA add authentication
### Add authorisation(based on roles)
