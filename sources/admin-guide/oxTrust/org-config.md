# Gluu Server UI ( oxTrust ) configuration 

oxTrust is a JBoss Seam application that provides organizational cloud identity
management services, including REST service endpoints and a user friendly cloud
identity management console (aka a GUI). 

oxTrust is tightly coupled with oxAuth. oxAuth configuration is stored in LDAP,
and it would be hard to generate the right configuration entries without
oxTrust. The projects are separate projects because in a high throughput cluster
deployment, many oxAuth servers are needed versus a few oxTrust instances.

In this page we are trying to highlight various features of Gluu oxTrust. 

## Configuration

### Organization Configuration

#### System Configuration:
System Configuration allows the Gluu Server administrator to choose various
options like “Authentication Mode” or “SCIM Support” to be enabled or disabled
system wide.

![Image](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/oxTrustConfiguration/Configuration/System_configuration.png?raw=true)

* _Authentication Mode_ : Various types of authentication methods can be chosen from this interface. Out of the box, the Gluu Server allows ‘basic’ username/password authentication against the server’s local LDAP or any remote Active Directory/LDAP. In addition to passwords, various commercial or custom strong authentication mechanisms can be enabled as well.

* _Authentication Level_ : Authentication level is a domain specific value that can be used to rate the relative security level for different authentication mechanisms. 

* _White Pages_ : If the Organization wants to use the Gluu Server’s built-in “White Pages” option, it can be enabled from here.

* _Federation Hosting_ : By default federation hosting is enabled. However, federation creation and operation can be complicated. Gluu offers an additional service called Federation Registry for those organizations interested in our assistance utilizing this feature.

* _Cache Refresh_ : “Cache Refresh” is a Gluu mechanism that pulls and syncs user information from a remote LDAP / Active Directory with the Gluu Server’s local LDAP. The Gluu Server administrator needs to provide sufficient information including username/password in Cache Refresh configuration before enabling this option. The documentation can be found [here](http://www.gluu.org/docs/admin-guide/user-management/ldap-sync/).

* _SCIM Configuration_ : If organization currently has an identity management or provisioning system in place, by using the SCIM protocol your organization can push and sync all relevant identity information to the Gluu Server. Documentation is available [here](http://www.gluu.org/docs/admin-guide/user-management/scim/).

* _DNS Server(s)_ : Organization can add DNS server info here.

* _Maximum Log Size_ : This option can be used to help mitigate space issues within the Gluu Server. The Gluu Server will automatically zip any logs which are greater than defined value of this field. i.e: If Gluu Server Administrator use 200MB for “Maximum Log Size”, Gluu Server will automatically start zipping those files which are / will be more than 200MB.

### Manage Certificate

There are various types of certificates here in Gluu Server. All can be managed
from oxTrust GUI. [Here](http://www.gluu.org/docs/admin-guide/certificates/) is
the documentation which is providing corresponding documentation. 

### Manage Authentication

Out of the box, the Gluu Server supports username/password authentication
against the local LDAP or a remote Active Directory/LDAP. In addition, oxTrust
provides the interface for inserting Jython code to enable dynamic
authentication logic, including the use of any strong, multi-step authentication
process. Gluu can write these scripts for premium customers and typically makes
the script open source for other organization’s use. Currently supported
two-factor authentication mechanisms can be found at: http://gluu.org/two-factor 

We have a complete separate section on
[this](http://www.gluu.org/docs/admin-guide/authentication/) subject. 

### Manage Registration

This is a new feature in Gluu Server. We are going to publish documentation on
this topi very soon. 

### SCIM Configuration

If organization currently has an identity management or provisioning system in
place, by using the SCIM protocol your organization can push and sync all
relevant identity information to the Gluu Server. Documentation is available
[here](http://www.gluu.org/docs/admin-guide/user-management/scim/).

### Import People

This feature allows the Gluu Server Administrator to bulk import users. Just
click on “Add” and upload the xls file. 

![Image](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/oxTrustConfiguration/Configuration/Import_people.png?raw=true)

Validation checking for the file can be done by using “Validate” button before
importing. If file is not correctly formatted, the server will reject the file
with an error as shown in the screenshot below. 

![Image](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/oxTrustConfiguration/Configuration/Import_people_failed.png?raw=true)


### Attributes

Documentation on LDAP Attribute is available [here](http://www.gluu.org/docs/admin-guide/saml/outbound-saml/#ldap-attributes). 


### Cache Refresh

Gluu Server Cache Refresh has a detailed documentation available. Can be checked
by [this](http://www.gluu.org/docs/admin-guide/user-management/ldap-sync/).


### Configure log viewer

Gluu Server has facility to read any log with GUI. Any log can be displayed from
Web UI with few clicks. To enable this feature click on “Configuration” → “Configure log viewer” 

Click on “Add log template”, two new boxes will appear. Left box is the
name/description of the log and right box require the real path of this log
file. As for example in the below image,  we are going to configure two logs: 1.
oxTrust log and 2. oxAuth log

![Image](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/oxTrustConfiguration/Configuration/Configure_Log_Viewer.png?raw=true)

### View log file

Log files which were configured in previous section can be viewed with this
“View log file” feature. Click “Configuration” → “View Log File”

![Image](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/oxTrustConfiguration/Configuration/View_Log_file.png?raw=true)

Now, select / click on desired allowed log file and insert a value for “Display
last lines count”. Gluu Server will show last 400 ( or, any selected value lines
) in GUI like below:

![Image](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/oxTrustConfiguration/Configuration/View_Log_file_2.png?raw=true)


### Configure Linktrack API


### Status

Status page shows the overall configuration of Gluu Server. A Gluu Server can
see the status of this IDP like below image. 

![Image](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/oxTrustConfiguration/Configuration/Status.png?raw=true)

Where:

* _Host name_ : The hostname of Gluu Server. The value of hostname is an unique identification number ( aka. Inum ) from Gluu Organization. 
* _IP address_ : The physical address of Gluu Server. 
* _System uptime_ : How long system has been maintaining it's healthy status. 
* _Last update_ : Time and date when Gluu Server's services were health checked. 
* _Polling interval_ : Time interval when Gluu Server reported it's status to Gluu's central LDAP server. 
* _Person count_ : How many users are here inside Gluu Server. 
* _Group count_ : How many active groups are here in Gluu Server. 
* _Free memory_ : Percentage of free memory. 
* _Free disk space_ : Percentage of free disk space. 

## SAML

### Trust Relationships

Documentation on Trust Relationship is available
[here](http://www.gluu.org/docs/admin-guide/saml/outbound-saml/#saml-trust-relationship). 

