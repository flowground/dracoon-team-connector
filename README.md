# ![LOGO](logo.png) DRACOON **flow**ground Connector

## Description

A generated **flow**ground connector for the DRACOON API (version 4.5.0).

Generated from: https://api.apis.guru/v2/specs/dracoon.team/4.5.0/swagger.json<br/>
Generated at: 2019-05-07T17:40:17+03:00

## API Description

REST Web Services for DRACOON.<br> Version. 4.5.0  - built at: 1517571015562

## Authorization

This API does not require authorization.

## Actions

### Authenticate user

> ### Functional Description:<br/>
> Authenticates user and provides an authentication token that is required for most operations.<br/>
> <br/>
> ### Precondition:<br/>
> Existing user that is not locked.<br/>
> <br/>
> ### Effects:<br/>
> User is logged in.<br/>
> <br/>
> ### Further Information:<br/>
> The provided token is valid for **2 hours**, every usage resets this period to 2 full hours again.  <br/>
> Logging off invalidates the token.  <br/>
> <br/>
> ### Important:  <br/>
> * If auth type `radius` is used, a token (request parameter) may be set, otherwise this parameter is ignored.  <br/>
> * If the token is set, `password` is optional for this auth type.<br/>
> <br/>
> ### Currently supported languages (with ISO 639-1 code):<br/>
> * German (de)<br/>
> * English (en)<br/>
> * Spanish (es)<br/>
> * French (fr)

*Tags:* `auth`

### Complete OpenID Connect authentication

> ### Functional Description:  <br/>
> This is the second step of the OpenID Connect authentication.  <br/>
> The user hands over the authorization code and is logged in.<br/>
> <br/>
> ### Precondition:<br/>
> Existing user with activated OpenID Connect authentication that is not locked.<br/>
> <br/>
> ### Effects:<br/>
> User is logged in.<br/>
> <br/>
> ### Further Information:<br/>
> See [http://openid.net/developers/specs](http://openid.net/developers/specs) for further information.

*Tags:* `auth`

#### Input Parameters
* `code` - _required_ - Authorization code
* `state` - _required_ - Authentication state

### Get OpenID Connect authentication resources

> ### Functional Description:  <br/>
> Provides information about OpenID Connect authentication options.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `auth`

### Ping

> ### Functional Description:<br/>
> Test connection to DRACOON Server.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> `200 OK` with current date string is returned if successful.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `auth`

### Request password reset

> ### Functional Description:  <br/>
> Request an email with a request token for a certain user to reset his / her password.<br/>
> <br/>
> ### Precondition:<br/>
> Registered user account.<br/>
> <br/>
> ### Effects:<br/>
> Provided user receives email with reset token.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Currently supported languages (with ISO 639-1 code):<br/>
> * German (de)<br/>
> * English (en)<br/>
> * Spanish (es)<br/>
> * French (fr)

*Tags:* `auth`

### Get information for password reset

> ### Functional Description:  <br/>
> Request all information for a password change dialogue e.g. real name of user.<br/>
> <br/>
> ### Precondition:<br/>
> User received a password reset token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `auth`

#### Input Parameters
* `token` - _required_ - Password reset token

### Reset password

> ### Functional Description:  <br/>
> Resets a user's password to a new value.<br/>
> <br/>
> ### Precondition:<br/>
> User received a password reset token.<br/>
> <br/>
> ### Effects:<br/>
> Newly transmitted password is set.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `auth`

#### Input Parameters
* `token` - _required_ - Password reset token

### Get authentication resources

> ### Functional Description:  <br/>
> Provides information about authentication options.<br/>
> <br/>
> ### Precondition: <br/>
> None.<br/>
> <br/>
> ### Effects: <br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> The server identifies the relevant customer by the passed HTTP header `Origin`.  <br/>
> Use this call to customize the log-on form.  <br/>
> <br/>
> ### Important: <br/>
> The default language and authentication method are always provided as topmost entry.<br/>
> <br/>
> ### Currently supported languages (with ISO 639-1 code):<br/>
> * German (de)<br/>
> * English (en)<br/>
> * Spanish (es)<br/>
> * French (fr)

*Tags:* `auth`

### Get authentication settings

> ### Functional Description:  <br/>
> Retrieve the settings of authentication configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read global config"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Configuration settings for various authentication methods<br/>
> <br/>
> ### Authentication Methods<br/>
> <br/>
> * **sql**  <br/>
>     **Basic Authentication globally allowed**  <br/>
>     This option must be activated to allow users to log in with their credentials stored in the database.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **active_directory**  <br/>
>     **Active Directory Authentication globally allowed**  <br/>
>     This option must be activated to allow users to log in with their Active Directory credentials.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **radius**  <br/>
>     **RADIUS Authentication globally allowed**  <br/>
>     This option must be activated to allow users to log in with their RADIUS username, their PIN and a token password.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **openid**  <br/>
>     **OpenID Connect Authentication globally allowed**  <br/>
>     This option must be activated to allow users to log in with their OpenID Connect identity.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **default_auth_method**  <br/>
>     **Default authentication method without user context**  <br/>
>     If this option is set, the chosen method will be provided as default authentication method if no user context is available.  <br/>
>     Only one authentication method can be set and it must be allowed (see above).  <br/>
>     If no value is set, there is no guarantee about the order of the returned methods.  <br/>
>     Only activated authentication methods may be set as default authentication method.  <br/>
>     VALUE: `[sql|active_directory|radius|openid]`<br/>
> <br/>
> ### Configurable settings for RADIUS authentication<br/>
> <br/>
> ### `DEPRECATED`<br/>
> <br/>
> These settings will be ignored.  <br/>
> Please use `/system/config/auth/radius` API.<br/>
> <br/>
> * **radius-ip**  <br/>
>     IP address of the RADIUS server  <br/>
>     VALUE: `IPv4 address`<br/>
> <br/>
> * **radius-port**  <br/>
>     Port of the RADIUS server (usually 1812)  <br/>
>     VALUE: `Port`<br/>
> <br/>
> * **radius-sharedsec**  <br/>
>     Shared Secret to access the RADIUS server  <br/>
>     VALUE: `Shared Secret`<br/>
> <br/>
> * **radius-otpPinFirst**  <br/>
>     Sequence order of concatenated PIN and One-Time token  <br/>
>     VALUE: `[true|false]`

*Tags:* `config`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Change authentication setting

> ### Functional Description:<br/>
> Change one or more settings of authentication configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change global config"_ required.<br/>
> <br/>
> ### Effects:<br/>
> One or more global authentication setting gets changed.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Configuration settings for various authentication methods<br/>
> <br/>
> ### Authentication Methods<br/>
> <br/>
> * **sql**  <br/>
>     **Basic Authentication globally allowed**  <br/>
>     This option must be activated to allow users to log in with their credentials stored in the database.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **active_directory**  <br/>
>     **Active Directory Authentication globally allowed**  <br/>
>     This option must be activated to allow users to log in with their Active Directory credentials.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **radius**  <br/>
>     **RADIUS Authentication globally allowed**  <br/>
>     This option must be activated to allow users to log in with their RADIUS username, their PIN and a token password.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **openid**  <br/>
>     **OpenID Connect Authentication globally allowed**  <br/>
>     This option must be activated to allow users to log in with their OpenID Connect identity.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **default_auth_method**  <br/>
>     **Default authentication method without user context**  <br/>
>     If this option is set, the chosen method will be provided as default authentication method if no user context is available.  <br/>
>     Only one authentication method can be set and it must be allowed (see above).  <br/>
>     If no value is set, there is no guarantee about the order of the returned methods.  <br/>
>     Only activated authentication methods may be set as default authentication method.  <br/>
>     VALUE: `[sql|active_directory|radius|openid]`<br/>
> <br/>
> ### Configurable settings for RADIUS authentication<br/>
> <br/>
> ### `DEPRECATED`<br/>
> <br/>
> These settings will be ignored.  <br/>
> Please use `PUT /system/config/auth/radius` API.<br/>
> <br/>
> * **radius-ip**  <br/>
>     IP address of the RADIUS server  <br/>
>     VALUE: `IPv4 address`<br/>
> <br/>
> * **radius-port**  <br/>
>     Port of the RADIUS server (usually 1812)  <br/>
>     VALUE: `Port`<br/>
> <br/>
> * **radius-sharedsec**  <br/>
>     Shared Secret to access the RADIUS server  <br/>
>     VALUE: `Shared Secret`<br/>
> <br/>
> * **radius-otpPinFirst**  <br/>
>     Sequence order of concatenated PIN and One-Time token  <br/>
>     VALUE: `[true|false]`

*Tags:* `config`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get system settings

> ### Functional Description:  <br/>
> DRACOON configuration entry point.  <br/>
> Returns a list of configurable system settings.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read global config"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> <br/>
> ### Attention<br/>
> If `eula_active` is true, but not accepted yet, or password must be changed, only the following two values are returned:<br/>
> * **allow_system_global_weak_password**<br/>
> * **eula_active**<br/>
> <br/>
> ### Configurable settings<br/>
> <br/>
> * **allow_system_global_weak_password**  <br/>
>     Allow weak password<br/>
>     * A weak password has to fulfill the following criteria:  <br/>
>         * is at least 8 characters long  <br/>
>         * contains letters and numbers<br/>
>     * A strong password has to fulfill the following criteria in addition:  <br/>
>         * contains at least one special character  <br/>
>         * contains upper and lower case characters<br/>
> <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **branding_server_branding_id** **`NEW`**  <br/>
>     The branding UUID, which corresponds to _BRANDING-QUALIFIER_ in the new branding server.  <br/>
>     VALUE: `String`<br/>
> <br/>
> * **branding_portal_url** **`NEW`**  <br/>
>     Access URL to to the Branding Portal.  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `String`<br/>
> <br/>
> * **branding_server_customer**  <br/>
>     The UUID of the branding server customer, which corresponds to customer key in the branding server.  <br/>
>     VALUE: `String`<br/>
> <br/>
> * **branding_server_url**  <br/>
>     Access URL to to the Branding Server.  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `String`<br/>
> <br/>
> * **connect_as_drive**  <br/>
>     Rooms can be mounted by WebDAV.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **dblog**  <br/>
>     Write logs to local database  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **default_downloadshare_expiration_period**  <br/>
>     Default expiration period for Download Shares in days.  <br/>
>     VALUE: `Integer between 0 and 9999`<br/>
> <br/>
> * **default_file_upload_expiration_date**  <br/>
>     Default expiration period for all uploaded files in days.  <br/>
>     VALUE: `Integer between 0 and 9999` (set 0 to disable)<br/>
> <br/>
> * **default_language**  <br/>
>     Define which language should be default.  <br/>
>     VALUE: `cf. GET /auth/resources Model "Language"`<br/>
> <br/>
> * **default_uploadshare_expiration_period**  <br/>
>     Default expiration period for Upload Shares in days.  <br/>
>     VALUE: `Integer between 0 and 9999`<br/>
> <br/>
> * **email_from**  <br/>
>     Sender of system-generated emails  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `Valid email address`<br/>
> <br/>
> * **email_to_sales**  <br/>
>     Contact email address for customers to request more user licenses or data volume.  <br/>
>     VALUE: `Valid email address`<br/>
> <br/>
> * **email_to_support**  <br/>
>     Support email address for users.  <br/>
>     VALUE: `Valid email address`<br/>
> <br/>
> * **enable_client_side_crypto**  <br/>
>     Activation status of **TripleCrypt(tm) Technology**.  <br/>
>     Can only be enabled once; disabling is not possible.  <br/>
>     VALUE: `[true|false]` (default: `false`)<br/>
> <br/>
> * **eula_active**  <br/>
>     Each user has to confirm the EULA at first login.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **eventlog_retention_period**  <br/>
>     Retention period (in days) of event log entries.  <br/>
>     After that period, all entries are deleted.  <br/>
>     Recommended value: 7  <br/>
>     VALUE: `Integer between 0 and 9999` (if set to 0: no logs are deleted)<br/>
> <br/>
> * **file_size_js**  <br/>
>     Maximum file size (in bytes) for downloads of encrypted files with JavaScript.  <br/>
>     Bigger files will require a JavaApplet.  <br/>
>     Recommended value: 10485760 (= 10MB)  <br/>
>     VALUE: `Integer`<br/>
> <br/>
> * **ip_address_logging**  <br/>
>     Determines whether a user's IP address is logged on login.  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **mailserver**  <br/>
>     Email server to send emails  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `DNS name or IPv4 of an email server`<br/>
> <br/>
> * **mailserver_authentication_necessary**  <br/>
>     Set to true if the email server requires authentication.  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **mailserver_password**  <br/>
> **Password is no longer returned.**<br/>
> <br/>
> * **mailserver_password_set**  <br/>
>     Indicates if a password is set for the mailserver (because `mailserver_password` is always returned empty)  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **mailserver_port**  <br/>
>     Email server port  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `Positive number`<br/>
> <br/>
> * **mailserver_username**  <br/>
>     User name for email server  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `User name for authentication`<br/>
> <br/>
> * **mailserver_use_ssl**  <br/>
>     Email server requires SSL connection?  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     Requires mailserver_use_starttls to be false  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **mailserver_use_starttls**  <br/>
>     Email server requires StartTLS connection?  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     Requires mailserver_use_ssl to be false  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **syslog**  <br/>
>     Write logs to a syslog interface  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **syslog_host**  <br/>
>     Syslog Server (IP or FQDN)  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `DNS name or IPv4 of a syslog server`<br/>
> <br/>
> * **syslog_port**  <br/>
>     Syslog server port  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `Positive Number`<br/>
> <br/>
> * **syslog_protocol**  <br/>
>     Protocol to connect to syslog server  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[TCP|UDP]`<br/>
> <br/>
> * **system_name**  <br/>
>     System name  <br/>
>     VALUE: `Display name of the DRACOON`<br/>
> <br/>
> * **enable_email_notification_button**  <br/>
>     Enable mail notification button  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **allow_share_password_sms**  <br/>
>     Allow sending of share passwords via SMS  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **globally_allow_share_password_sms**  <br/>
>     Allow sending of share passwords via SMS  <br/>
>     Read only  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **use_s3_storage**  <br/>
>     Defines if S3 is used as storage backend  <br/>
>     Read only  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **s3_default_region**  <br/>
>     Suggested S3 region  <br/>
>     Read only  <br/>
>     VALUE: `Region name`

*Tags:* `config`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Change system settings

> ### Functional Description:<br/>
> DRACOON configuration entry point.  <br/>
> Returns a list of configurable settings.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change global config"_ required.<br/>
> <br/>
> ### Effects:<br/>
> One or more global authentication setting gets changed.<br/>
> <br/>
> ### Further Information:<br/>
> <br/>
> ### Attention<br/>
> Only visible for _Config Manager_ of Provider Customer.<br/>
> <br/>
> ### Settings<br/>
> <br/>
> ### Configurable settings<br/>
> <br/>
> * **allow_system_global_weak_password**  <br/>
>     Allow weak password<br/>
>     * A weak password has to fulfill the following criteria:  <br/>
>         * is at least 8 characters long  <br/>
>         * contains letters and numbers<br/>
>     * A strong password has to fulfill the following criteria in addition:  <br/>
>         * contains at least one special character  <br/>
>         * contains upper and lower case characters<br/>
> <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **branding_server_branding_id** **`NEW`**  <br/>
>     The branding UUID, which corresponds to _BRANDING-QUALIFIER_ in the new branding server.  <br/>
>     VALUE: `String`<br/>
> <br/>
> * **branding_portal_url** **`NEW`**  <br/>
>     Access URL to to the Branding Portal.  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `String`<br/>
> <br/>
> * **branding_server_customer**  <br/>
>     The UUID of the branding server customer, which corresponds to customer key in the branding server.  <br/>
>     VALUE: `String`<br/>
> <br/>
> * **branding_server_url**  <br/>
>     Access URL to to the Branding Server.  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `String`<br/>
> <br/>
> * **connect_as_drive**  <br/>
>     Rooms can be mounted by WebDAV.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **dblog**  <br/>
>     Write logs to local database  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **default_downloadshare_expiration_period**  <br/>
>     Default expiration period for Download Shares in days.  <br/>
>     VALUE: `Integer between 0 and 9999`<br/>
> <br/>
> * **default_file_upload_expiration_date**  <br/>
>     Default expiration period for all uploaded files in days.  <br/>
>     VALUE: `Integer between 0 and 9999` (set 0 to disable)<br/>
> <br/>
> * **default_language**  <br/>
>     Define which language should be default.  <br/>
>     VALUE: `cf. GET /auth/resources Model "Language"`<br/>
> <br/>
> * **default_uploadshare_expiration_period**  <br/>
>     Default expiration period for Upload Shares in days.  <br/>
>     VALUE: `Integer between 0 and 9999`<br/>
> <br/>
> * **email_from**  <br/>
>     Sender of system-generated emails  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `Valid email address`<br/>
> <br/>
> * **email_to_sales**  <br/>
>     Contact email address for customers to request more user licenses or data volume.  <br/>
>     VALUE: `Valid email address`<br/>
> <br/>
> * **email_to_support**  <br/>
>     Support email address for users.  <br/>
>     VALUE: `Valid email address`<br/>
> <br/>
> * **enable_client_side_crypto**  <br/>
>     Activation status of **TripleCrypt(tm) technology**.  <br/>
>     Can only be enabled once; disabling is not possible.  <br/>
>     VALUE: `[true|false]` (default: `false`)<br/>
> <br/>
> * **eula_active**  <br/>
>     Each user has to confirm the EULA at first login.  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **eventlog_retention_period**  <br/>
>     Retention period (in days) of event log entries.  <br/>
>     After that period, all entries are deleted.  <br/>
>     Recommended value: 7  <br/>
>     VALUE: `Integer between 0 and 9999` (if set to 0: no logs are deleted)<br/>
> <br/>
> * **file_size_js**  <br/>
>     Maximum file size (in bytes) for downloads of encrypted files with JavaScript.  <br/>
>     Bigger files will require a JavaApplet.  <br/>
>     Recommended value: 10485760 (= 10MB)  <br/>
>     VALUE: `Integer`<br/>
> <br/>
> * **ip_address_logging**  <br/>
>     Determines whether a user's IP address is logged on login.  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **mailserver**  <br/>
>     Email server to send emails  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `DNS name or IPv4 of an email server`<br/>
> <br/>
> * **mailserver_authentication_necessary**  <br/>
>     Set to true if the email server requires authentication.  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **mailserver_password**  <br/>
>     Password for email server  <br/>
>     VALUE: `Password for authentication`<br/>
> <br/>
> * **mailserver_port**  <br/>
>     Email server port  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `Positive number`<br/>
> <br/>
> * **mailserver_username**  <br/>
>     User name for email server  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `User name for authentication`<br/>
> <br/>
> * **mailserver_use_ssl**  <br/>
>     Email server requires SSL connection?  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     Requires mailserver_use_starttls to be false  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **mailserver_use_starttls**  <br/>
>     Email server requires StartTLS connection?  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     Requires mailserver_use_ssl to be false  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **syslog**  <br/>
>     Write logs to a syslog interface  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **syslog_host**  <br/>
>     Syslog Server (IP or FQDN)  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `DNS name or IPv4 of a syslog server`<br/>
> <br/>
> * **syslog_port**  <br/>
>     Syslog server port  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `Positive Number`<br/>
> <br/>
> * **syslog_protocol**  <br/>
>     Protocol to connect to syslog server  <br/>
>     Only visible for _Config Manager_ of Provider Customer  <br/>
>     VALUE: `[TCP|UDP]`<br/>
> <br/>
> * **system_name**  <br/>
>     System name  <br/>
>     VALUE: `Display name of the DRACOON`<br/>
> <br/>
> * **enable_email_notification_button**  <br/>
>     Enable mail notification button  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **allow_share_password_sms**  <br/>
>     Allow sending of share passwords via SMS  <br/>
>     VALUE: `[true|false]`

*Tags:* `config`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Download ZIP file

> ### Functional Description:  <br/>
> Download multiple files in a ZIP archive.<br/>
> <br/>
> ### Precondition:<br/>
> Valid download token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Create a download token with `POST /nodes/zip`.

*Tags:* `downloads`

#### Input Parameters
* `token` - _required_ - Download token

### Download file

> ### Functional Description:  <br/>
> Download a file.<br/>
> <br/>
> ### Precondition:<br/>
> Valid download token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Range requests are supported (please cf. [RCF 7233](https://tools.ietf.org/html/rfc7233) for details).

*Tags:* `downloads`

#### Input Parameters
* `token` - _required_ - Download token
* `Range` - _optional_ - Range
* `generic_mimetype` - _optional_ - Always return 'application/octet-stream' instead of specific mimetype

### Download file

> ### Functional Description:  <br/>
> Download a file.<br/>
> <br/>
> ### Precondition:<br/>
> Valid download token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Range requests are supported (please cf. [RCF 7233](https://tools.ietf.org/html/rfc7233) for details).

*Tags:* `downloads`

#### Input Parameters
* `token` - _required_ - Download token
* `Range` - _optional_ - Range
* `generic_mimetype` - _optional_ - Always return 'application/octet-stream' instead of specific mimetype

### Get node assigned users with permissions

> ### Functional Description:  <br/>
> Retrieve a list of all nodes of type `room` and the room assignment users with permissions.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read audit log"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE`  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **nodeId**  <br/>
>     Node ID  <br/>
>     OPERATOR: `eq` (Node ID equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **nodeName**  <br/>
>     Node name (Login)  <br/>
>     OPERATOR: `cn|eq` (Node name contains value | equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **nodeParentId**  <br/>
>     Node parent ID  <br/>
>     OPERATOR: `eq` (Parent ID equal value; parent ID 0 is the root node.)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **userId**  <br/>
>     User ID  <br/>
>     OPERATOR: `eq` (User ID equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **userName**  <br/>
>     User name (Login)  <br/>
>     OPERATOR: `cn|eq` (User name contains value | equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **userFirstName**  <br/>
>     User first name  <br/>
>     OPERATOR: `cn|eq` (User first name contains value | equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **userLastName**  <br/>
>     User last name  <br/>
>     OPERATOR: `cn|eq` (User last name contains value | equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **permissionsManage**  <br/>
>     Filter the users that (don't) have manage right in this room  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **nodeIsEncrypted**  <br/>
>     Encrypted node filter  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **nodeHasRecycleBin**  <br/>
>     Recycle bin filter  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
>     <br/>
> * **nodeHasActivitiesLog**  <br/>
>     Activities log filter  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> ### Logical grouping:<br/>
> Filtering according first three fields (`login`, `lastName`, `firstName`) is intrinsically processed by the API as logical _OR_.  <br/>
> In opposite, filtering according to is processed intrinsically as logical _AND_.<br/>
> <br/>
> ### Example:<br/>
> * `userName:cn:searchString_1|userFirstName:cn:searchString_2|nodeId:eq:2`  <br/>
> Filter by user login containing `searchString_1` OR first name containing `searchString_2` and node ID equal 2.<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **nodeId**: Node ID<br/>
> * **nodeName**: Node name<br/>
> * **nodeParentId**: Node parent ID<br/>
> * **nodeSize**: Node size<br/>
> * **nodeQuota**: Node quota<br/>
> <br/>
> ### Example:<br/>
> * `nodeName:asc`  <br/>
> Sort by `nodeName` ascending.

*Tags:* `eventlog`

#### Input Parameters
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get system events

> ### Functional Description:  <br/>
> Retrieve eventlog (= audit log) events.<br/>
> <br/>
> ### Precondition:<br/>
> Role _"Log Auditor"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Output may be limited to a certain number of entries.  <br/>
> Please use filter criteria and paging.

*Tags:* `eventlog`

#### Input Parameters
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `date_start` - _optional_ - Start date
e.g. 2015-12-31T23:59:00
* `date_end` - _optional_ - End date
e.g. 2015-12-31T23:59:00
* `type` - _optional_ - Operation ID
cf. `GET /eventlog/operations`
* `user_id` - _optional_ - User ID
* `status` - _optional_ - Operation status:
* 0 - Success
* 2 - Error
* `user_client` - _optional_ - User client
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get allowed Log Operations

> ### Functional Description:  <br/>
> Retrieve eventlog (= audit log) operation IDs and the associated log operation description.<br/>
> <br/>
> ### Precondition:<br/>
> Role _"Log Auditor"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `eventlog`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get user groups

> ### Functional Description:  <br/>
> Returns a list of user groups.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filters<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE`<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **name**  <br/>
>     Group name  <br/>
>     OPERATOR: `cn` (Group name contains value; multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> ### Example: <br/>
> * `name:cn:searchString`  <br/>
> Filter by group `name` containing `searchString`.<br/>
> <br/>
> ### Sorting<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **name**: Group name<br/>
> * **createdAt**: Creation date<br/>
> * **expireAt**: Expiration date<br/>
> * **cntUsers**: Amount of users<br/>
> <br/>
> ### Example:<br/>
> * `name:asc|expireAt:desc`  <br/>
> Sort by `name` ascending and by `expireAt` descending.

*Tags:* `groups`

#### Input Parameters
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Create new user group

> ### Functional Description:<br/>
> Create a new user group.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> A new group is created.<br/>
> <br/>
> ### Further Information:<br/>
> * If a group should not expire, leave `expireAt` empty.<br/>
> * Group names are limited to **150** characters<br/>
> * Allowed characters: **All**

*Tags:* `groups`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete user group

> ### Functional Description:<br/>
> Delete a user group.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"delete groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> User group is deleted.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `groups`

#### Input Parameters
* `group_id` - _required_ - Group ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get user group

> ### Functional Description:  <br/>
> Retrieve detailed information about one user group.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `groups`

#### Input Parameters
* `group_id` - _required_ - Group ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Update user group

> ### Functional Description:  <br/>
> Update the meta data of a user group.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Meta data of a user group is updated.<br/>
> <br/>
> ### Further Information:<br/>
> * If a group should not expire, leave `expireAt` empty.<br/>
> * Group names are limited to **150** characters<br/>
> * Allowed characters: **All**

*Tags:* `groups`

#### Input Parameters
* `group_id` - _required_ - Group ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get group roles

> ### Functional Description:  <br/>
> Retrieve a list of all roles and the role assignment rights of a group.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `groups`

#### Input Parameters
* `group_id` - _required_ - Group ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get rooms granted to the group or/and rooms that can be granted

> ### Functional Description:  <br/>
> Retrieve a list of rooms, that are granted or may be granted to the group.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **name**  <br/>
>     Room name  <br/>
>     OPERATOR: `cn` (multiple values not allowed)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **isGranted**  <br/>
>     Filter rooms which the group is or is not granted  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `true`)<br/>
> <br/>
> * **effectivePerm**  <br/>
>     Filter rooms with _DIRECT_ or _DIRECT_ **AND** _EFFECTIVE_ permissions  <br/>
>     * `false`: _DIRECT_ permissions  <br/>
>     * `true`:  _DIRECT_ **AND** _EFFECTIVE_ permissions  <br/>
>     <br/>
>     > _DIRECT_ means: e.g. room administrator grants read permissions to group of users **directly** on desired room.  <br/>
>     _EFFECTIVE_ means: e.g. group of users gets read permissions on desired room through **inheritance**.  <br/>
> <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]` (default: `true`)<br/>
> <br/>
> ### Example:<br/>
> * `isGranted:eq:false|name:cn:searchString`  <br/>
> Get all rooms where the group is not granted AND whose `name` is like `searchString`.

*Tags:* `groups`

#### Input Parameters
* `group_id` - _required_ - Group ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete group members

> ### Functional Description:  <br/>
> Remove group members.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Provided users are removed from the user group.<br/>
> <br/>
> ### Further Information:<br/>
> Batch function.  <br/>
> The provided users are removed from the user group.

*Tags:* `groups`

#### Input Parameters
* `group_id` - _required_ - Group ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get group member users or/and users who can become a member

> ### Functional Description:  <br/>
> Retrieve a list of group members.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **displayName**  <br/>
>     User display name (`firstName`, `lastName`, `login`)  <br/>
>     OPERATOR: `cn` (multiple values not allowed)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **isMember**  <br/>
>     Filter the group members AND / OR users  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `true`)<br/>
> <br/>
> ### Example:<br/>
> * `is_member:eq:false|displayName:cn:searchString`  <br/>
> Get all users that are not in this group AND whose display name is like `searchString`.

*Tags:* `groups`

#### Input Parameters
* `group_id` - _required_ - Group ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Add group members

> ### Functional Description:<br/>
> Add members to a group.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> New members are added to the group.<br/>
> <br/>
> ### Further Information:<br/>
> Batch function.  <br/>
> The newly provided members will be added to the existing ones.

*Tags:* `groups`

#### Input Parameters
* `group_id` - _required_ - Group ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete file system nodes

> ### Functional Description:<br/>
> Delete nodes (room, folder, file).<br/>
> <br/>
> ### Precondition:<br/>
> Authenticated user with _"delete"_ permissions on supplied nodes.<br/>
> <br/>
> ### Effects:<br/>
> Nodes are deleted.<br/>
> <br/>
> ### Further Information:<br/>
> Nodes must be in same parent.

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get file system nodes

> ### Functional Description:  <br/>
> Provides a hierarchical list of file system nodes (rooms, folders, files) of a given parent that are accessible by the current user.<br/>
> <br/>
> ### Precondition:<br/>
> Authenticated user.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> `EncryptionInfo` is not provided.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE[:VALUE...]`<br/>
> <br/>
> ### Fields:<br/>
> <br/>
> * **type**  <br/>
>     Node type filter  <br/>
>     OPERATOR: `eq` (multiple values allowed)  <br/>
>     VALUE: `[room|folder|file]`<br/>
> <br/>
> * **perm**  <br/>
>     Permissions filter  <br/>
>     OPERATOR: `eq` (multiple values allowed)  <br/>
>     VALUE: `[manage|read|change|create|delete|manageDownloadShare|manageUploadShare|canReadRecycleBin|canRestoreRecycleBin|canDeleteRecycleBin]`<br/>
> <br/>
> * **childPerm**  <br/>
>     The same as **perm**, but less restrictive (applied to child nodes only)  <br/>
>     OPERATOR: `eq` (multiple values allowed)  <br/>
>     VALUE: `[manage|read|change|create|delete|manageDownloadShare|manageUploadShare|canReadRecycleBin|canRestoreRecycleBin|canDeleteRecycleBin]`<br/>
> <br/>
> * **name**  <br/>
>     Node name filter  <br/>
>     OPERATOR: `cn` (name contains value, multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **encrypted**  <br/>
>     Node encryption status filter  <br/>
>     OPERATOR: `eq` (Node is encrypted, multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **branchVersion**  <br/>
>     Node branch version  <br/>
>     OPERATOR: `ge|le`  <br/>
>     VALUE: `version number`<br/>
> <br/>
> ### Example:<br/>
> * `type:eq:room:folder|perm:eq:read`  <br/>
> Get nodes where type equals `room` OR `folder` AND user has `read` permissions.<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields not supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **name**: Node name<br/>
> * **createdBy**: Creator user name<br/>
> * **createdAt**: Creation date<br/>
> * **updatedBy**: Modifier user name<br/>
> * **updatedAt**: Modification date<br/>
> * **fileType**: File type (extension)<br/>
> * **classification**: Classification ID (for files only):  <br/>
>     * 1 - public<br/>
>     * 2 - for internal use only<br/>
>     * 3 - confidential<br/>
>     * 4 - strictly confidential<br/>
> * **size**: Node size<br/>
> * **cntAdmins**: **DEPRECATED (No effect)** For rooms only: Number of admins<br/>
> * **cntUsers**: **DEPRECATED (No effect)** For rooms only: Number of users<br/>
> * **nodeCntChildren**: For rooms / folders only: Number of direct children (not recursive)<br/>
> * **cntDeletedVersions**: For files / folders only: Number of deleted versions of this file / folder (not recursive)<br/>
> <br/>
> ### Example:<br/>
> * `name:desc`  <br/>
> Sort by `name` descending.

*Tags:* `nodes`

#### Input Parameters
* `depth_level` - _optional_ - * 0 - top level nodes only
* n (any positive number) - include n levels starting from the current node
* -1 - full tree (**DEPRECATED**: will be removed)
* `parent_id` - _optional_ - Parent node ID.
Only rooms and folders can be parents.
Parent ID 0 or empty is the root node.
* `room_manager` - _optional_ - Show all rooms for management perspective.
Only posible for _Rooms Managers_.
For all other users, it will be ignored.
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete nodes from Recycle Bin

> ### Functional Description:<br/>
> Permanently remove a list of nodes from the Recycle Bin.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"delete recycle bin"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> All provided nodes are removed.<br/>
> <br/>
> ### Further Information:<br/>
> The removal of deleted nodes from the Recycle Bin is irreversible.

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Restore deleted nodes

> ### Functional Description:  <br/>
> Restore a list of deleted nodes.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"create"_ permissions in parent room and _"restore recycle bin"_ permissions.<br/>
> <br/>
> ### Effects:<br/>
> The selected files are moved from the Recycle Bin to the chosen productive container.<br/>
> <br/>
> ### Further Information:<br/>
> If no parent ID is provided, the node is restored to its previous location.  <br/>
> The default resolution strategy is `autorename` that adds numbers to the file name until the conflict is solved.  <br/>
> If an existing file is overwritten, it is moved to the Recycle Bin instead of the restored one.

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get deleted node

> ### Functional Description:  <br/>
> Get the meta data of one deleted node.<br/>
> <br/>
> ### Precondition:<br/>
> User can access parent room and has _"read recycle bin"_ permissions.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `deleted_node_id` - _required_ - Deleted node ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Set FileKeys for a list of users and files

> ### Functional Description:  <br/>
> Sets symmetric file keys for several users and files.<br/>
> <br/>
> ### Precondition:<br/>
> User has file keys for the files.<br/>
> <br/>
> ### Effects:<br/>
> Stores new file keys for other users.<br/>
> <br/>
> ### Further Information:<br/>
> Only users with copies of the file key (encrypted with their public keys) can access a certain file.  <br/>
> This endpoint is used for the distribution of file keys amongst an authorized user base.

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Create new file upload channel

> ### Functional Description:<br/>
> This endpoint creates a new upload channel which is the first step in any file upload workflow.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"create"_ permissions in the parent container (room or folder).<br/>
> <br/>
> ### Effects:<br/>
> A new upload channel for a file is created.  <br/>
> Its ID and an upload token are returned.<br/>
> <br/>
> ### Further Information:<br/>
> The upload ID is used for uploads with `X-Sds-Auth-Token` header, the upload token can be used for uploads without authentication header.<br/>
> <br/>
> Please provide the size of the intended upload so that the quota can be checked in advanced and no data is transferred unnecessarily.<br/>
> <br/>
> ### Node naming convention<br/>
> <br/>
> * Node (room, folder, file) names are limited to 150 characters.<br/>
> <br/>
> * Not allowed names:  <br/>
> `'CON', 'PRN', 'AUX', 'NUL', 'COM1', 'COM2', 'COM3', 'COM4', 'COM5', 'COM6', 'COM7', 'COM8', 'COM9', 'LPT1', 'LPT2', 'LPT3', 'LPT4', 'LPT5', 'LPT6', 'LPT7', 'LPT8', 'LPT9','.','/'`<br/>
> <br/>
> * Not allowed characters in names:  <br/>
> `'../', '\\', '<','>', ':', '\"', '|', '?', '*', '/'`

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Cancel file upload

> ### Functional Description:<br/>
> Cancel an upload and destroy the Upload Channel.<br/>
> <br/>
> ### Precondition:<br/>
> An Upload Channel has been created.<br/>
> <br/>
> ### Effects:<br/>
> The Upload Channel is removed and all temporary uploaded data is purged.<br/>
> <br/>
> ### Further Information:<br/>
> It is recommended to notify the API about cancelled uploads if possible.

*Tags:* `nodes`

#### Input Parameters
* `upload_id` - _required_ - Upload channel ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Upload file

> ### Functional Description:  <br/>
> Uploads a file or parts of it in an active Upload Channel.<br/>
> <br/>
> ### Precondition:<br/>
> An Upload Channel has been created.<br/>
> <br/>
> ### Effects:<br/>
> A file or parts of it are uploaded to a temporary location.<br/>
> <br/>
> ### Further Information:<br/>
> This endpoints supports chunked upload.  <br/>
> Please cf. [RFC 7233](https://tools.ietf.org/html/rfc7233) for further information.

*Tags:* `nodes`

#### Input Parameters
* `upload_id` - _required_ - Upload channel ID
* `Content-Range` - _optional_ - Content-Range
e.g. "bytes 0-999/3980"
cf. [RFC 7233](https://tools.ietf.org/html/rfc7233)
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Complete file upload

> ### Functional Description:<br/>
> Finishes an upload and closes the corresponding Upload Channel.<br/>
> <br/>
> ### Precondition:<br/>
> An Upload Channel has been created and data has been transmitted.<br/>
> <br/>
> ### Effects:<br/>
> The upload is finished and the temporary file is moved to the productive environment.<br/>
> <br/>
> ### Further Information:<br/>
> The provided file name might be changed in accordance with the resolution strategy:  <br/>
> * **autorename**: changes the file name and adds a number to avoid conflicts.<br/>
> * **overwrite**: deletes any old file with the same file name.<br/>
> * **fail**: returns an error; in this case, another `PUT` request with a different file name may be sent.<br/>
> <br/>
> Please ensure that all chunks have been transferred correctly before finishing the upload.<br/>
> <br/>
> ### 200 OK is not used by this API

*Tags:* `nodes`

#### Input Parameters
* `upload_id` - _required_ - Upload channel ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Update file meta data

> ### Functional Description:  <br/>
> Updates a file's meta data.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"change"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> Meta data changed.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Node naming convention<br/>
> <br/>
> * Node (room, folder, file) names are limited to 150 characters.<br/>
> <br/>
> * Not allowed names:  <br/>
> `'CON', 'PRN', 'AUX', 'NUL', 'COM1', 'COM2', 'COM3', 'COM4', 'COM5', 'COM6', 'COM7', 'COM8', 'COM9', 'LPT1', 'LPT2', 'LPT3', 'LPT4', 'LPT5', 'LPT6', 'LPT7', 'LPT8', 'LPT9','.','/'`<br/>
> <br/>
> * Not allowed characters in names:  <br/>
> `'../', '\\', '<','>', ':', '\"', '|', '?', '*', '/'`

*Tags:* `nodes`

#### Input Parameters
* `file_id` - _required_ - File ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get room emergency password

> ### Functional Description:  <br/>
> Returns the file key for the room emergency password of a certain file (if available).<br/>
> <br/>
> ### Precondition:<br/>
> User with _"read"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `file_id` - _required_ - File ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get system emergency password

> ### Functional Description:  <br/>
> Returns the file key for the system emergency password of a certain file (if available).<br/>
> <br/>
> ### Precondition:<br/>
> User with _"read"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `file_id` - _required_ - File ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Download file

> ### Use `downloads` API<br/>
> <br/>
> ### Functional Description:<br/>
> Download a file.<br/>
> <br/>
> ### Precondition:<br/>
> User with _"read"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Range requests are supported (please cf. [RFC 7233](https://tools.ietf.org/html/rfc7233) for details).

*Tags:* `nodes`

#### Input Parameters
* `file_id` - _required_ - File ID
* `Range` - _optional_ - Range
* `generic_mimetype` - _optional_ - Always return 'application/octet-stream' instead of specific mimetype
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Download file

> ### Use `downloads` API<br/>
> <br/>
> ### Functional Description:<br/>
> Download a file.<br/>
> <br/>
> ### Precondition:<br/>
> User with _"read"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Range requests are supported (please cf. [RFC 7233](https://tools.ietf.org/html/rfc7233) for details).

*Tags:* `nodes`

#### Input Parameters
* `file_id` - _required_ - File ID
* `Range` - _optional_ - Range
* `generic_mimetype` - _optional_ - Always return 'application/octet-stream' instead of specific mimetype
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Generate download token

> ### Functional Description:<br/>
> Create a download token to retrieve a file without `X-Sds-Auth-Token` Header.<br/>
> <br/>
> ### Precondition:<br/>
> User with _"read"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> Download token is generated and returned.<br/>
> <br/>
> ### Further Information:<br/>
> The token is necessary to access `downloads` ressources.

*Tags:* `nodes`

#### Input Parameters
* `file_id` - _required_ - File ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get user's file key

> ### Functional Description:  <br/>
> Returns the file key for the current user (if available).<br/>
> <br/>
> ### Precondition:<br/>
> User with _"read"_, _"create"_ or _"manage download share"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> The symmetric file key is encrypted with the user's public key.  <br/>
> File keys are generated with the workflow _"Generate file keys"_ that starts at `GET /nodes/missingFileKeys`.

*Tags:* `nodes`

#### Input Parameters
* `file_id` - _required_ - File ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Create new folder

> ### Functional Description:<br/>
> Creates a new folder.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"create"_ permissions in current room.<br/>
> <br/>
> ### Effects:<br/>
> A new folder is created.<br/>
> <br/>
> ### Further Information:<br/>
> Folders cannot be created on top level (without parent element).<br/>
> <br/>
> ### Node naming convention<br/>
> <br/>
> * Node (room, folder, file) names are limited to 150 characters.<br/>
> <br/>
> * Not allowed names:  <br/>
> `'CON', 'PRN', 'AUX', 'NUL', 'COM1', 'COM2', 'COM3', 'COM4', 'COM5', 'COM6', 'COM7', 'COM8', 'COM9', 'LPT1', 'LPT2', 'LPT3', 'LPT4', 'LPT5', 'LPT6', 'LPT7', 'LPT8', 'LPT9','.','/'`<br/>
> <br/>
> * Not allowed characters in names:  <br/>
> `'../', '\\', '<','>', ':', '\"', '|', '?', '*', '/'`

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Update folder

> ### Functional Description:  <br/>
> Renames an existing folder.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"change"_ permissions in current room.<br/>
> <br/>
> ### Effects:<br/>
> The folder is renamed.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Node naming convention<br/>
> <br/>
> * Node (room, folder, file) names are limited to 150 characters.<br/>
> <br/>
> * Not allowed names:  <br/>
> `'CON', 'PRN', 'AUX', 'NUL', 'COM1', 'COM2', 'COM3', 'COM4', 'COM5', 'COM6', 'COM7', 'COM8', 'COM9', 'LPT1', 'LPT2', 'LPT3', 'LPT4', 'LPT5', 'LPT6', 'LPT7', 'LPT8', 'LPT9','.','/'`<br/>
> <br/>
> * Not allowed characters in names:  <br/>
> `'../', '\\', '<','>', ':', '\"', '|', '?', '*', '/'`

*Tags:* `nodes`

#### Input Parameters
* `folder_id` - _required_ - Folder ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get files where the user has no filekey

> ### Functional Description:  <br/>
> Requests a list of missing file keys that may be generated by the current user.<br/>
> <br/>
> ### Precondition:<br/>
> User has a key pair.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Clients should regularly request missing file keys to provide access to files for other users.  <br/>
> The returned list is ordered by priority (emergency passwords are returned first).  <br/>
> ### Please note: <br/>
> This API returns **1024** entries at maximum.  <br/>
> There might be more entries even if a total of 1024 is returned.

*Tags:* `nodes`

#### Input Parameters
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `room_id` - _optional_ - Room ID
* `file_id` - _optional_ - File ID
* `user_id` - _optional_ - User ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Create new room

> ### Functional Description:<br/>
> Creates a new room at the provided parent node.  <br/>
> Creation of top level rooms provided.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"create"_ permissions in the parent room.<br/>
> <br/>
> ### Effects:<br/>
> A new room is created.<br/>
> <br/>
> ### Further Information:  <br/>
> Rooms may only have other rooms as parent.  <br/>
> Rooms on top level do not have any parent.  <br/>
> Rooms may have rooms as children on n hierarchy levels.  <br/>
> If permission inheritance is disabled, there must be at least one admin user / group (with neither the group nor the user having an expiration date).

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get user-room assignments per group that have not been accepted yet

> ### Functional Description:  <br/>
> Requests a list of user-room assignments by groups that have not been approved yet  <br/>
> These can have the state:<br/>
> * **WAITING**  <br/>
> * **DENIED**  <br/>
> * **ACCEPTED**  <br/>
> <br/>
> **ACCEPTED** assignments are already removed from the list.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Room administrators should regularly request pending assingments to provide access to rooms for other users.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE[:VALUE...]`<br/>
> <br/>
> ### Fields:<br/>
> <br/>
> * **userId**  <br/>
>     User ID filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **groupId**  <br/>
>     Group ID filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **roomId**  <br/>
>     Room ID filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **state**  <br/>
>     Assignment state  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `[WAITING|DENIED]`<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields not supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **userId**: User ID<br/>
> * **groupId**: Group ID<br/>
> * **roomId**: Room ID<br/>
> * **state**: State<br/>
> <br/>
> ### Example:<br/>
> * `userId:desc`  <br/>
> Sort by user ID descending.

*Tags:* `nodes`

#### Input Parameters
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Handle user-room assignments per group that have not been accepted yet

> ### Functional Description:  <br/>
> Handles a list of user-room assignments by groups that have not been approved yet  <br/>
> **WAITING** or **DENIED** assignments can be **ACCEPTED**.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> User-room assignment is approved and the user gets access to the group.<br/>
> <br/>
> ### Further Information:<br/>
> Room administrators should regularly handle pending assignments to provide access to rooms for other users.

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Update room

> ### Functional Description:  <br/>
> Update a room's meta data.<br/>
> <br/>
> ### Precondition:<br/>
> User is admin in superordinated level.<br/>
> <br/>
> ### Effects:<br/>
> Room's meta data is changed.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Node naming convention<br/>
> <br/>
> * Node (room, folder, file) names are limited to 150 characters.<br/>
> <br/>
> * Not allowed names:  <br/>
> `'CON', 'PRN', 'AUX', 'NUL', 'COM1', 'COM2', 'COM3', 'COM4', 'COM5', 'COM6', 'COM7', 'COM8', 'COM9', 'LPT1', 'LPT2', 'LPT3', 'LPT4', 'LPT5', 'LPT6', 'LPT7', 'LPT8', 'LPT9','.','/'`<br/>
> <br/>
> * Not allowed characters in names:  <br/>
> `'../', '\\', '<','>', ':', '\"', '|', '?', '*', '/'`

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get events of a room

> ### Use `nodes/rooms/{room_id}/events` API<br/>
> <br/>
> ### Functional Description:<br/>
> Retrieve syslog (= audit log) events related to a room.<br/>
> <br/>
> ### Precondition:<br/>
> Requires _"read"_ permissions on that room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Output may be limited to a certain number of entries.  <br/>
> Please use filter criteria and paging.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `date_start` - _optional_ - Start date
e.g. 2015-12-31T23:59:00
* `date_end` - _optional_ - End date
e.g. 2015-12-31T23:59:00
* `type` - _optional_ - Operation ID
cf. `GET /eventlog/operations`
* `user_id` - _optional_ - User ID
* `status` - _optional_ - Operation status:
* 0 - Success
* 2 - Error
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Config room

> ### Functional Description:<br/>
> Updates a room.<br/>
> <br/>
> ### Precondition:<br/>
> User needs to be room administrator.<br/>
> <br/>
> ### Effects:<br/>
> Room's configuration is changed.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Encrypt room

> ### Functional Description:  <br/>
> Activates the client-side encryption for a room.<br/>
> <br/>
> ### Precondition:<br/>
> User needs to be room administrator.<br/>
> <br/>
> ### Effects:<br/>
> Encryption of room is activated.<br/>
> <br/>
> ### Further Information:<br/>
> Only empty rooms at the top level may be encrypted.  <br/>
> This endpoint may also be used to disable encryption of an empty room.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get events of a room

> ### Use `nodes/rooms/{room_id}/events` API<br/>
> <br/>
> ### Functional Description:<br/>
> Retrieve syslog (= audit log) events related to a room.<br/>
> <br/>
> ### Precondition:<br/>
> Requires _"read"_ permissions on that room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Output may be limited to a certain number of entries.  <br/>
> Please use filter criteria and paging.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `date_start` - _optional_ - Start date
e.g. 2015-12-31T23:59:00
* `date_end` - _optional_ - End date
e.g. 2015-12-31T23:59:00
* `type` - _optional_ - Operation ID
cf. `GET /eventlog/operations`
* `user_id` - _optional_ - User ID
* `status` - _optional_ - Operation status:
* 0 - Success
* 2 - Error
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Revoke group permissions from room

> ### Functional Description:  <br/>
> Batch function.  <br/>
> Revoke groups from room.<br/>
> <br/>
> ### Precondition:<br/>
> User needs to be room administrator.<br/>
> <br/>
> ### Effects:<br/>
> Group's permissions are revoked.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get room granted groups or/and groups that can be granted

> ### Functional Description:  <br/>
> Retrieve a list of groups that are and / or can be granted to the room.<br/>
> <br/>
> ### Precondition:<br/>
> Any permissions on target room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **name**  <br/>
>     Group name  <br/>
>     OPERATOR: `cn` (multiple values not allowed)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **isGranted**  <br/>
>     Filter the groups that have (no) access to this room  <br/>
>     **Attention! This filter is only available for room administrators.  <br/>
>     Other users can only look for groups in their rooms, so this filter is true and cannot be overridden.**  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `true`)<br/>
> <br/>
> * **permissionsManage**  <br/>
>     Filter the groups that (don't) have manage right in this room  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`.<br/>
> <br/>
> * **effectivePerm**  <br/>
>     Filter groups with _DIRECT_ or _DIRECT_ **AND** _EFFECTIVE_ permissions  <br/>
>     * `false`: _DIRECT_ permissions  <br/>
>     * `true`:  _DIRECT_ **AND** _EFFECTIVE_ permissions  <br/>
>     <br/>
>     > _DIRECT_ means: e.g. room administrator grants read permissions to group of users **directly** on desired room.  <br/>
>     _EFFECTIVE_ means: e.g. group of users gets read permissions on desired room through **inheritance**.  <br/>
> <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]` (default: `true`)<br/>
> <br/>
> * **groupId**  <br/>
>     Filter the groups by ID  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> ### Example:<br/>
> * `isGranted:eq:false|name:cn:searchString`  <br/>
> Get all groups that have no rights to this room of AND whose name is like `searchString`.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Add or change room granted groups

> ### Functional Description:<br/>
> Batch function.  <br/>
> All existing group permissions will be overwritten.<br/>
> <br/>
> ### Precondition:<br/>
> User needs to be room administrator.<br/>
> <br/>
> ### Effects:<br/>
> Group's permissions are changed.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get room emergency password

> ### Functional Description:  <br/>
> Retrieve the room emergency password.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"read"_ permissions in that room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Revoke user permissions from room

> ### Functional Description:  <br/>
> Batch function.  <br/>
> Revoke users from room.<br/>
> <br/>
> ### Precondition:<br/>
> User needs to be room administrator.<br/>
> <br/>
> ### Effects:<br/>
> User's permissions are revoked.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get room granted users or/and users that can be granted

> ### Functional Description:  <br/>
> Retrieve a list of users that are and / or can be granted to the room.<br/>
> <br/>
> ### Precondition:<br/>
> Any permissions on target room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **displayName**  <br/>
>     User display name (`firstName`, `lastName`, `login`)  <br/>
>     OPERATOR: `cn` (multiple values not allowed)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **isGranted**  <br/>
>     Filter the users that have (no) access to this room  <br/>
>     **Attention! This filter is only available for room administrators.  <br/>
>     Other users can only look for users in their rooms, so this filter is true and cannot be overridden.**  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `true`)<br/>
> <br/>
> * **permissionsManage**  <br/>
>     Filter the users that (don't) have manage right in this room  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`.<br/>
> <br/>
> * **effectivePerm**  <br/>
>     Filter users with _DIRECT_ or _DIRECT_ **AND** _EFFECTIVE_ permissions  <br/>
>     * `false`: _DIRECT_ permissions  <br/>
>     * `true`:  _DIRECT_ **AND** _EFFECTIVE_ permissions  <br/>
>     * `any`: _DIRECT_ **AND** _EFFECTIVE_ **AND** _OVER GROUP_ permissions  <br/>
>     <br/>
>     > _DIRECT_ means: e.g. room administrator grants read permissions to user **directly** on desired room.  <br/>
>     _EFFECTIVE_ means: e.g. user gets read permissions on desired room through **inheritance**.  <br/>
>     _OVER GROUP_ means: e.g. user gets read permissions on desired room through **group membership**.  <br/>
> <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `false`)<br/>
> <br/>
> * **userId**  <br/>
>     Filter the users by ID  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> ### Example:<br/>
> * `isGranted:eq:true|displayName:cn:searchString|permissions_manage:eq:true`  <br/>
> Get all users that have manage rights to this room of AND whose name is like `searchString`.<br/>
> <br/>
> ### The filters are connected by AND

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Add or change room granted users

> ### Functional Description:<br/>
> Batch function.  <br/>
> All existing user permissions will be overwritten.<br/>
> <br/>
> ### Precondition:<br/>
> User needs to be room administrator.<br/>
> <br/>
> ### Effects:<br/>
> User's permissions are changed.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `room_id` - _required_ - Room ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Search file system nodes

> ### Functional Description:  <br/>
> Provides a flat list of file system nodes (rooms, folders, files) of a given parent that are accessible by the current user.<br/>
> <br/>
> ### Precondition:<br/>
> Authenticated user with _"read"_ permissions on parent room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:  <br/>
> A maximum of **500** results is returned.  <br/>
> For more results please use paging (`offset` + `limit`).  <br/>
> `EncryptionInfo` is not provided.  <br/>
> Wildcard character is the asterisk character: `*`.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE[:VALUE...]`<br/>
> <br/>
> ### Fields:<br/>
> <br/>
> * **type**  <br/>
>     Node type filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `[room|folder|file]`<br/>
> <br/>
> * **fileType**  <br/>
>     File type filter (file extension)  <br/>
>     OPERATOR: `cn` (name contains value, multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **classification**  <br/>
>     File classification filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `[1|2|3|4]`<br/>
>     * 1 - public<br/>
>     * 2 - for internal use only<br/>
>     * 3 - confidential<br/>
>     * 4 - strictly confidential<br/>
> <br/>
> * **createdBy**  <br/>
>     Creation username filter  <br/>
>     OPERATOR: `cn` (name contains value, multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **createdAt**  <br/>
>     Creation data filter  <br/>
>     OPERATOR: `ge|le`  <br/>
>     VALUE: `Date (yyyy-MM-dd)`<br/>
> <br/>
> * **updatedBy**  <br/>
>     Last change username filter  <br/>
>     OPERATOR: `cn` (name contains value, multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **updatedAt**  <br/>
>     Last change date filter  <br/>
>     OPERATOR: `ge|le`  <br/>
>     VALUE: `Date (yyyy-MM-dd)`<br/>
> <br/>
> * **expireAt**  <br/>
>     Expire date filter  <br/>
>     OPERATOR: `ge|le`  <br/>
>     VALUE: `Date (yyyy-MM-dd)`<br/>
> <br/>
> * **size**  <br/>
>     Size filter  <br/>
>     OPERATOR: `ge|le`  <br/>
>     VALUE: `Size in bytes`<br/>
> <br/>
> * **isFavorite**  <br/>
>     Favorite filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **branchVersion**  <br/>
>     Node branch version  <br/>
>     OPERATOR: `ge|le`  <br/>
>     VALUE: `Version Number`<br/>
> <br/>
> ### Example:<br/>
> * `type:eq:file|createdAt:ge:2015-01-01`  <br/>
> Get nodes where `type` equals `file` AND file was created at or after `2015-01-01`.<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`   <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields not supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **name**: Node name<br/>
> * **createdBy**: Creator user name<br/>
> * **createdAt**: Creation date<br/>
> * **updatedBy**: Modifier user name<br/>
> * **updatedAt**: Modification date<br/>
> * **fileType**: File type (extension)<br/>
> * **classification**: Classification ID (for files only):  <br/>
>     * 1 - public<br/>
>     * 2 - for internal use only<br/>
>     * 3 - confidential<br/>
>     * 4 - strictly confidential<br/>
> * **size**: Node size<br/>
> * **cntAdmins**: **DEPRECATED (No Effect)** For rooms only: Number of admins<br/>
> * **cntUsers**: **DEPRECATED (No Effect)** For rooms only: Number of users<br/>
> * **nodeCntChildren**: For rooms / folders only: Number of direct children (not recursive)<br/>
> * **cntDeletedVersions**: For files / folders only: Number of deleted versions of this file/folder (not recursive)<br/>
> * **type**: Node type (room, folder, file)<br/>
> <br/>
> ### Example:<br/>
> * `name:desc`  <br/>
> Sort by `name` descending.

*Tags:* `nodes`

#### Input Parameters
* `search_string` - _required_ - Search string
* `depth_level` - _optional_ - * 0 - top level nodes only
* -1 - full tree
* n (any positive number) - include n levels starting from the current node
* `parent_id` - _optional_ - Parent node ID.
Only rooms and folders can be parents.
Parent ID 0 or empty is the root node.
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Generate download token for zip download

> ### Functional Description:  <br/>
> Create a download token to retrieve several files in one ZIP archive.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"read"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> Download token is generated and returned.<br/>
> <br/>
> ### Further Information:<br/>
> The token is necessary to access `downloads` resources.  <br/>
> ZIP download is only available for files and folders.

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Download files/folders as ZIP

> ### Functional Description:  <br/>
> Download multiple files in a ZIP archive.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Delete file system node

> ### Functional Description:<br/>
> Delete node (room, folder, file).<br/>
> <br/>
> ### Precondition:<br/>
> Authenticated user with _"delete"_ permissions on supplied nodes.<br/>
> <br/>
> ### Effects:<br/>
> Node gets deleted.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Node ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get node

> ### Functional Description:  <br/>
> Get node (room, folder, file).<br/>
> <br/>
> ### Precondition:<br/>
> User has _"read"_ permissions in auth parent room.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Node ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Copy file system nodes

> ### Functional Description:<br/>
> Copies nodes (folder, file) to another parent.<br/>
> <br/>
> ### Precondition:<br/>
> Authenticated user with _"read"_ permissions in the source parent and _"create"_ permissions in the target parent node.<br/>
> <br/>
> ### Effects:<br/>
> Nodes are copied to target parent.<br/>
> <br/>
> ### Further Information:<br/>
> Nodes must be in same source parent.  <br/>
> Rooms cannot be copied.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Target parent node ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Empty Recycle Bin

> ### Functional Description:  <br/>
> Empty a Recycle Bin.<br/>
> <br/>
> ### Precondition:<br/>
> User has _"delete recycle bin"_ permissions in parent room.<br/>
> <br/>
> ### Effects:<br/>
> All files in the Recycle Bin are permanently removed.<br/>
> <br/>
> ### Further Information:<br/>
> Actually removes the previously deleted files from the system.  <br/>
> This action is irreversible.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Parent node ID.
Only rooms and folders can be parents.
Parent ID 0 or empty is the root node.
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get deleted nodes

> ### Functional Description:  <br/>
> Retrieve a list of deleted nodes in a Recycle Bin.<br/>
> <br/>
> ### Precondition:<br/>
> User can access parent room and has _"read recycle bin"_ permissions.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Only room IDs are accepted as node ID since only rooms have Recycle Bins.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE[:VALUE...]`<br/>
> <br/>
> ### Fields:<br/>
> <br/>
> * **type**  <br/>
>     Node type filter  <br/>
>     OPERATOR: `eq` (multiple values allowed)  <br/>
>     VALUE: `[folder|file]`<br/>
> <br/>
> * **name**  <br/>
>     Node name filter  <br/>
>     OPERATOR: `cn` (Node name contains value, multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **parentPath**  <br/>
>     Parent path filter  <br/>
>     OPERATOR: `cn` (Parent path contains value, multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> ### Example:<br/>
> * `type:eq:file:folder|name:cn:searchString_1|parentPath:cn:searchString_2`  <br/>
> Get deleted nodes where type equals `file` or `folder` AND deleted node name containing `searchString_1` AND deleted node parent path containing `searchString 2`.<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields not supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **name**: Node name<br/>
> * **cntVersions**: Number of deleted versions of this file<br/>
> * **firstDeletedAt**: First deleted version<br/>
> * **lastDeletedAt**: Last deleted version<br/>
> * **parentPath**: Parent path of deleted node<br/>
> <br/>
> ### Example:<br/>
> * `name:desc`  <br/>
> Sort by `name` descending.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Auth parent node ID
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get deleted versions

> ### Functional Description:  <br/>
> Retrieve all deleted versions of a node.<br/>
> <br/>
> ### Precondition:<br/>
> User can access parent room and has _"read recycle bin"_ permissions.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> The node is identified by three parameters:<br/>
> * parent ID<br/>
> * name<br/>
> * type (file, folder).<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields not supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **expireAt**:Expiration date<br/>
> * **accessedAt**: Last access date<br/>
> * **size**: Node size<br/>
> * **classification**: Classification ID (for files only):  <br/>
>     * 1 - public<br/>
>     * 2 - for internal use only<br/>
>     * 3 - confidential<br/>
>     * 4 - strictly confidential<br/>
> * **createdAt**: Creation date<br/>
> * **createdBy**: Node created by user<br/>
> * **updatedAt**: Modification date<br/>
> * **updatedBy**: Node modified by user<br/>
> * **deletedAt**: Deleted date<br/>
> * **deletedBy**: Node deleted by user<br/>
> <br/>
> ### Example:<br/>
> * `expireAt:desc`  <br/>
> Sort by `expireAt` descending.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Auth parent node ID
* `type` - _required_ - Node type
    Possible values: file, folder.
* `name` - _required_ - Node name
* `sort` - _optional_ - Sort string
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Unmark a node (room, folder or file) as favorite

> ### Functional Description:<br/>
> Unmarks a node (room, folder, file) as favorite.<br/>
> <br/>
> ### Precondition:<br/>
> User needs _"read"_ permissions on that node.<br/>
> <br/>
> ### Effects:<br/>
> A node gets unmarked as favorite.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Node ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Mark a node (room, folder or file) as favorite

> ### Functional Description:  <br/>
> Marks a node (room, folder, file) as favorite.<br/>
> <br/>
> ### Precondition:<br/>
> User needs _"read"_ permissions on that node.<br/>
> <br/>
> ### Effects:<br/>
> A node gets marked as favorite.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Node ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Move file system nodes

> ### Functional Description:  <br/>
> Moves nodes (folder, file) to another parent.<br/>
> <br/>
> ### Precondition:<br/>
> Authenticated user with _"read"_ and _"delete"_ permissions in the source parent and _"create"_ permissions in the target parent node.<br/>
> <br/>
> ### Effects:<br/>
> Nodes are moved to target parent.<br/>
> <br/>
> ### Further Information:<br/>
> Nodes must be in same source parent.  <br/>
> Rooms cannot be moved.

*Tags:* `nodes`

#### Input Parameters
* `node_id` - _required_ - Target parent node ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get customers

> ### Functional Description:  <br/>
> Receive a list of customers.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> This list returns a maximum of **1000** entries.  <br/>
> Please use filters or searches to specify what you are looking for.  <br/>
> Authentication with `X-Sds-Service-Token` required.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE[:VALUE...]`<br/>
> <br/>
> ### Fields:<br/>
> <br/>
> * **id**  <br/>
>     Customer ID filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **companyName**  <br/>
>     Company name filter  <br/>
>     OPERATOR: `cn` (Company name contains value, multiple values not allowed)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **customerContractType**  <br/>
>     Customer contract type filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `demo|free|pay`<br/>
> <br/>
> * **activationCode**  <br/>
>     Activation code filter  <br/>
>     OPERATOR: `cn|eq` (Activation code contains value | equals value, multiple values not allowed )  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **trialDaysLeft**  <br/>
>     Left trial days filter  <br/>
>     OPERATOR: `ge|le` (Number of trial days is greater or equal | less or equal)  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **providerCustomerId**  <br/>
>     Provider Customer ID filter  <br/>
>     OPERATOR: `cn|eq` (providerCustomerId contains value | equals value, multiple values not allowed )  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **quotaMax**  <br/>
>     Maximum quota filter  <br/>
>     OPERATOR: `ge|le` (Quota is greater or equal | less or equal)  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **quotaUsed**  <br/>
>     Used quota filter  <br/>
>     OPERATOR: `ge|le` (Quota is greater or equal | less or equal)  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **userMax**  <br/>
>     Maximum user filter  <br/>
>     OPERATOR: `ge|le` (User maximum is greater or equal | less or equal)  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **userUsed**  <br/>
>     Used users filter  <br/>
>     OPERATOR: `ge|le` (Number of registered users is greater or equal | less or equal)  <br/>
>     VALUE: `Positive Integer`<br/>
> <br/>
> * **lockStatus**  <br/>
>     Lock status filter  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `Integer (0 or 1)`<br/>
> <br/>
> * **createdAt**  <br/>
>     Creation date filter  <br/>
>     OPERATOR: `ge|le` (Date is greater or equal | less or equal)  <br/>
>     VALUE: `Date`<br/>
> <br/>
> * **updatedAt**  <br/>
>     Update date filter  <br/>
>     OPERATOR: `ge|le` (Date is greater or equal | less or equal)  <br/>
>     VALUE: `Date`<br/>
> <br/>
> * **lastLoginAt**  <br/>
>     Last login filter  <br/>
>     OPERATOR: `ge|le` (Date is greater or equal | less or equal)  <br/>
>     VALUE: `Date`<br/>
> <br/>
> * **userLogin**  <br/>
>     User login filter  <br/>
>     OPERATOR: `eq` (Customer user login name equal value, multiple values not allowed)  <br/>
>     Search user all logins e.g. `sql`, `active_directory`, `radius`  <br/>
>     VALUE: `search string`<br/>
>     <br/>
> * **attributeKey**  <br/>
>     Customer attribute key filter  <br/>
>     OPERATOR: `eq` (Customer attribute key equal value, multiple values not allowed)  <br/>
>     Search customers with given customer attribute key.  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **attributeValue**  <br/>
>     Customer attribute value filter  <br/>
>     OPERATOR: `eq` (Customer attribute value equal value, multiple values not allowed)  <br/>
>     Search customers with given customer attribute value.  <br/>
>     VALUE: `search string`<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields not supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **companyName**: Company name<br/>
> * **customerContractType**: Customer contract type<br/>
> * **trialDaysLeft**: Number of remaining trial days (demo customers)<br/>
> * **providerCustomerId**: Provider Customer ID (pay customers)<br/>
> * **quotaMax**: Maximum quota<br/>
> * **quotaUsed**: Currently used quota<br/>
> * **userMax**: Maximum user number<br/>
> * **userUsed**: Number of currently active users<br/>
> * **lockStatus**: Lock status of customer<br/>
> * **createdAt**: Creation date<br/>
> * **updatedAt**: Date of last update<br/>
> * **lastLoginAt**: Date of last login of any user of this customer<br/>
> <br/>
> ### Example:<br/>
> * `companyName:desc`  <br/>
> Sort by company `name` descending.

*Tags:* `provisioning`

#### Input Parameters
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `include_attributes` - _optional_ - Include custom customer attributes.
* `X-Sds-Service-Token` - _required_ - Service Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Create customer

> ### Functional Description:<br/>
> Create a new customer.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> A new customer is created.<br/>
> <br/>
> ### Further Information:<br/>
> Authentication with `X-Sds-Service-Token` required.  <br/>
> If no company name is set, first name of the first administrator is used.  <br/>
> Max quota has to be at least 1 GB (= 1 073 741 824 B).<br/>
> <br/>
> ### Authentication Method Options<br/>
> <br/>
> * **SQL**  <br/>
>     `none`<br/>
> <br/>
> * **Active Directory**  <br/>
>     (optional)  <br/>
>     key: `"ad_config_id"`  <br/>
>     value: "Active Directory configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "Active Directory user name according to auth setting `userFilter`"<br/>
> <br/>
> * **RADIUS**  <br/>
>     key: `"username"`  <br/>
>     value: "Radius user name"<br/>
> <br/>
> * **OpenID Connect**  <br/>
>     key: `"openid_config_id"`  <br/>
>     value: "OpenID Connect configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "OpenID Connect user name according to auth setting `mappingClaim`"

*Tags:* `provisioning`

#### Input Parameters
* `X-Sds-Service-Token` - _required_ - Service Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete customer

> ### Functional Description:<br/>
> Delete a customer.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> Customer is deleted.<br/>
> <br/>
> ### Further Information:<br/>
> Authentication with `X-Sds-Service-Token` required.

*Tags:* `provisioning`

#### Input Parameters
* `customer_id` - _required_ - Customer ID
* `X-Sds-Service-Token` - _required_ - Service Authentication token

### Get customer

> ### Functional Description:  <br/>
> Receive details of a selected customer.<br/>
> <br/>
> ### Precondition:<br/>
> Existing customer.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Authentication with `X-Sds-Service-Token` required.

*Tags:* `provisioning`

#### Input Parameters
* `customer_id` - _required_ - Customer ID
* `include_attributes` - _optional_ - Include custom customer attributes.
* `X-Sds-Service-Token` - _required_ - Service Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Update customer

> ### Functional Description:  <br/>
> Change selected attributes of a customer.<br/>
> <br/>
> ### Precondition:<br/>
> Existing customer.<br/>
> <br/>
> ### Effects:<br/>
> Update of attributes.<br/>
> <br/>
> ### Further Information:<br/>
> Authentication with `X-Sds-Service-Token` required.

*Tags:* `provisioning`

#### Input Parameters
* `customer_id` - _required_ - Customer ID
* `X-Sds-Service-Token` - _required_ - Service Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Set customer attributes

> ### Functional Description:  <br/>
> Set custom customer attributes.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change global config"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Custom customer attributes gets set.<br/>
> <br/>
> ### Further Information:<br/>
> Batch function.  <br/>
> All existing customer attributes will be deleted.  <br/>
> Allowed characters for keys are: `[a-zA-Z0-9_-]`  <br/>
> Characters are case-insensitive.

*Tags:* `provisioning`

#### Input Parameters
* `customer_id` - _required_ - Customer ID
* `X-Sds-Service-Token` - _required_ - Service Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Add or edit customer attributes

> ### Functional Description:  <br/>
> Add or edit custom customer attributes.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change global config"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Custom customer attributes get added or edited.<br/>
> <br/>
> ### Further Information:<br/>
> Batch function.  <br/>
> If an entry exists before, it will be overwritten.  <br/>
> Allowed characters for keys are: `[a-zA-Z0-9_-]`  <br/>
> Characters are case-insensitive.

*Tags:* `provisioning`

#### Input Parameters
* `customer_id` - _required_ - Customer ID
* `X-Sds-Service-Token` - _required_ - Service Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete customer attributes

> ### Functional Description:<br/>
> Delete custom customer attribute.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change global config"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Custom customer attribute gets deleted.<br/>
> <br/>
> ### Further Information:<br/>
> Allowed characters for keys are: `[a-zA-Z0-9_-]`  <br/>
> Characters are case-insensitive.

*Tags:* `provisioning`

#### Input Parameters
* `customer_id` - _required_ - Customer ID
* `key` - _required_ - Key
* `X-Sds-Service-Token` - _required_ - Service Authentication token

### Get customer users

> ### Functional Description:  <br/>
> Receive a list of users associated with a certain customer.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Authentication with `X-Sds-Service-Token` required.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE`  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **login**  <br/>
>     Login name  <br/>
>     OPERATOR: `cn` (User login name contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **firstName**  <br/>
>     First name  <br/>
>     OPERATOR: `cn` (User first name contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **lastName**  <br/>
>     Last name  <br/>
>     OPERATOR: `cn` (User last name contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **lockStatus**  <br/>
>     Lock status:<br/>
>     * 0 - Locked<br/>
>     * 1 - Web access allowed<br/>
>     * 2 - Web and mobile access allowed,  <br/>
>     <br/>
>     OPERATOR: `eq` (User lock status)  <br/>
>     VALUE: `[0|1|2]`.<br/>
> <br/>
> * **effectiveRoles**  <br/>
>     Filter users with _DIRECT_ or _DIRECT_ **AND** _EFFECTIVE_ roles  <br/>
>     * `false`: _DIRECT_ roles  <br/>
>     * `true`:  _DIRECT_ **AND** _EFFECTIVE_ roles  <br/>
> <br/>
>     > _DIRECT_ means: e.g. user gets role **directly** granted from someone with _grant permission_ right.  <br/>
>     _EFFECTIVE_ means: e.g. user gets role through **group membership**.  <br/>
> <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]` (default: `false`)<br/>
> <br/>
> <br/>
> ### Logical grouping:<br/>
> Filtering according first three fields (`login`, `lastName`, `firstName`) is intrinsically processed by the API as logical _OR_.  <br/>
> In opposite, filtering according to last three field (`lockStatus`) is processed intrinsically as logical _AND_.<br/>
> <br/>
> ### Example:<br/>
> * `login:cn:searchString_1|firstName:cn:searchString_2|lockStatus:eq:2`  <br/>
> Filter by `login` contains `searchString_1` or `firstName` contains `searchString_2` and user are not locked.<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **login**: Login name<br/>
> * **firstName**: First name<br/>
> * **lastName**: Last name<br/>
> * **gender**: Gender<br/>
> * **lockStatus**: User lock status<br/>
> * **lastLoginSuccessAt**: Last successful logon date<br/>
> * **expireAt**: Expiration date<br/>
> <br/>
> ### Example:<br/>
> * `firstName:asc|lastLoginSuccessAt:desc`  <br/>
> Sort by `firstName` ascending and by `lastLoginSuccessAt` descending.

*Tags:* `provisioning`

#### Input Parameters
* `customer_id` - _required_ - Customer ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `X-Sds-Service-Token` - _required_ - Service Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get branding info

> ### Functional Description:  <br/>
> Public branding information.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> If `brandingServerBrandingId` is set, `brandingServerCustomer` is not supplied.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `public`

### Get public Download Share info

> ### Functional Description:  <br/>
> Retrieve the public information of a Download Share.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Generate download token

> ### Functional Description:<br/>
> Generate a download token to retrieve a shared file.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> Download token is generated and returned.<br/>
> <br/>
> ### Further Information:<br/>
> After generating the download token a download is possible with:<br/>
> * `GET /public/shares/downloads/{access_key}/{token}`

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key

### Download file

> ### Functional Description:  <br/>
> Download a file.<br/>
> <br/>
> ### Precondition:<br/>
> Valid download token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Range requests are supported (please cf. [RCF 7233](https://tools.ietf.org/html/rfc7233) for details).

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key
* `token` - _required_ - Download token
* `Range` - _optional_ - Range
* `generic_mimetype` - _optional_ - Always return 'application/octet-stream' instead of specific mimetype

### Download file

> ### Functional Description:  <br/>
> Download a file.<br/>
> <br/>
> ### Precondition:<br/>
> Valid download token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Range requests are supported (please cf. [RCF 7233](https://tools.ietf.org/html/rfc7233) for details).

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key
* `token` - _required_ - Download token
* `Range` - _optional_ - Range
* `generic_mimetype` - _optional_ - Always return 'application/octet-stream' instead of specific mimetype

### Get public Upload Share info

> ### Functional Description:  <br/>
> Provides information about the desired Upload Share.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> If no password is set, the returned information is reduced to the following attributes (if available):<br/>
> <br/>
> * **name**<br/>
> * **maxSlots**<br/>
> * **createdAt**<br/>
> * **isProtected**<br/>
> * **isEncrypted**<br/>
> * **showUploadedFiles**<br/>
> * **userUserPublicKeyList** (if parent is end-to-end encrypted)<br/>
> <br/>
> Only if the password is transmitted as `X-Sds-Share-Password` header, all values are returned.

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key
* `X-Sds-Share-Password` - _optional_ - Upload share password
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Create new file upload channel

> ### Functional Description:  <br/>
> Create a new upload channel.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> Upload channel is created and corresponding token / upload ID returned.<br/>
> <br/>
> ### Further Information:<br/>
> The token from the response can be used at:<br/>
> <br/>
> * `POST /uploads/{token}`<br/>
> * `PUT /uploads/{token}`<br/>
> * `DELETE /uploads/{token}`<br/>
> <br/>
> Please provide the size of the intended upload so that the quota can be checked in advanced and no data is transferred unnecessarily.<br/>
> <br/>
> ### Node naming convention<br/>
> <br/>
> * Node (room, folder, file) names are limited to 150 characters.<br/>
> <br/>
> * Not allowed names:  <br/>
> `'CON', 'PRN', 'AUX', 'NUL', 'COM1', 'COM2', 'COM3', 'COM4', 'COM5', 'COM6', 'COM7', 'COM8', 'COM9', 'LPT1', 'LPT2', 'LPT3', 'LPT4', 'LPT5', 'LPT6', 'LPT7', 'LPT8', 'LPT9','.','/'`<br/>
> <br/>
> * Not allowed characters in names:  <br/>
> `'../', '\\', '<','>', ':', '\"', '|', '?', '*', '/'`

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key

### Cancel file upload

> ### Functional Description:<br/>
> Abort (chunked) upload via Upload Share.<br/>
> <br/>
> ### Precondition:<br/>
> Valid Upload ID.<br/>
> <br/>
> ### Effects:<br/>
> Aborts upload and invalidates upload ID / token.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key
* `upload_id` - _required_ - Upload channel ID

### Upload file

> ### Functional Description:  <br/>
> Chunked upload of files via Upload Share.<br/>
> <br/>
> ### Precondition:<br/>
> Valid upload ID.<br/>
> <br/>
> ### Effects:<br/>
> Chunk of file is uploaded.<br/>
> <br/>
> ### Further Information:<br/>
> Chunked uploads (range requests) are supported (please cf. [RCF 7233](https://tools.ietf.org/html/rfc7233) for details).

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key
* `upload_id` - _required_ - Upload channel ID
* `Content-Range` - _optional_ - Content-Range
e.g. "bytes 0-999/3980"
cf. [RFC 7233](https://tools.ietf.org/html/rfc7233)
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Complete file upload

> ### Functional Description:<br/>
> Finalize (chunked) upload via Upload Share.<br/>
> <br/>
> ### Precondition:<br/>
> Valid upload ID.<br/>
> <br/>
> ### Effects:<br/>
> Finalizes upload.<br/>
> <br/>
> ### Further Information:<br/>
> Chunked uploads (range requests) are supported (please cf. [RCF 7233](https://tools.ietf.org/html/rfc7233) for details).  <br/>
> <br/>
> Please ensure that all chunks have been transferred correctly before finishing the upload.  <br/>
> If file hash has been created in time a `201 Created` will be responded and hash will be part of response, otherwise it will be a `202 Accepted` without it.<br/>
> <br/>
> ### 200 OK is not used by this API

*Tags:* `public`

#### Input Parameters
* `access_key` - _required_ - Access key
* `upload_id` - _required_ - Upload channel ID

### Get software version info

> ### Functional Description:  <br/>
> Public software version information.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> The version of DRACOON Server consists of two components:<br/>
> * **API**<br/>
> * **Core** (refered to as _"Server"_)<br/>
> <br/>
> that are versioned individually.

*Tags:* `public`

#### Input Parameters
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get system information

> ### Functional Description:  <br/>
> Provides information about system.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `public`

### Get Active Directory authentication information

> ### Functional Description:  <br/>
> Provides information about Active Directory authentication options.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `public`

### Get OpenID Connect authentication information

> ### Functional Description:  <br/>
> Provides information about OpenID Connect authentication options.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `public`

### Get system time

> ### Functional Description:  <br/>
> Retrieve the actual server time.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `public`

#### Input Parameters
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get all roles and to the role assignment rights

> ### Functional Description:  <br/>
> Retrieve a list of all Roles and the role assignment rights.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `roles`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Revoke groups role

> ### Functional Description:  <br/>
> Removes one or more groups from a role.<br/>
> <br/>
> ### Precondition:<br/>
> Role _"Group Manager"_ required.  <br/>
> For each role, at least one non-expiring user must remain who keeps the role.<br/>
> <br/>
> ### Effects:<br/>
> One or more groups will be removed from a role.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `roles`

#### Input Parameters
* `role_id` - _required_ - Role ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get role groups

> ### Functional Description:  <br/>
> Get all groups of a role.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **isMember**  <br/>
>     Filter the groups which are / aren't member of that role  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `true`)<br/>
> <br/>
> * **name**  <br/>
>     Group name  <br/>
>     OPERATOR: `cn` (Group name contains value; multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> ### Example:<br/>
> * `isMember:eq:false|name:cn:searchString`  <br/>
> Get all groups that are not a member of that role AND whose `name` contains `searchString`.

*Tags:* `roles`

#### Input Parameters
* `role_id` - _required_ - Role ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Add groups to the role

> ### Functional Description:<br/>
> Adds one or more groups to a role.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"grant permission on groups"_ required.<br/>
> <br/>
> ### Effects:<br/>
> One or more groups will be added to a role.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `roles`

#### Input Parameters
* `role_id` - _required_ - Role ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Revoke users role

> ### Functional Description:  <br/>
> Removes one or more users from a role.<br/>
> <br/>
> ### Precondition:<br/>
> Role _"User Manager"_ required.  <br/>
> For each role, at least one non-expiring user must remain who keeps the role.<br/>
> <br/>
> ### Effects:<br/>
> One or more users will be removed from a role.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `roles`

#### Input Parameters
* `role_id` - _required_ - Role ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get role users

> ### Functional Description:  <br/>
> Get all users of a role.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **isMember**  <br/>
>     Filter the users which are / aren't member of that role  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `true`)<br/>
> <br/>
> * **displayName**  <br/>
>     User display name (firstName, lastName, login)  <br/>
>     OPERATOR: `cn` (User display name contains value; multiple values not allowed)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> ### Example:<br/>
> * `isMember:eq:false|displayName:cn:searchString`  <br/>
> Get all users that are not member of that role AND whose display name contains `searchString`.

*Tags:* `roles`

#### Input Parameters
* `role_id` - _required_ - Role ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Add users to the role

> ### Functional Description:<br/>
> Adds one or more users to a role.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"grant permission on users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> One or more users will be added to a role.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `roles`

#### Input Parameters
* `role_id` - _required_ - Role ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get Download Shares

> ### Functional Description:  <br/>
> Retrieve a list of Download Shares.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filters<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE`  <br/>
> Multiple fields is supported.<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **name**  <br/>
>     Alias Name or File Name  <br/>
>     OPERATOR: `cn` ( name contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **createdBy**  <br/>
>     Creator info  <br/>
>     OPERATOR: `cn` (Creator info (`login`, `email`, `firstName`, `lastName`) contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **accessKey**  <br/>
>     Share access key  <br/>
>     OPERATOR: `cn` (Share access key contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **nodeId**  <br/>
>     Source node ID  <br/>
>     OPERATOR: `eq` (Source file / folder / room ID)  <br/>
>     VALUE: `Search node ID`<br/>
> <br/>
> * **userId**  <br/>
>     Creator user ID  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `Search user ID`<br/>
> <br/>
> ### Example:<br/>
> * `name:cn:searchString_1|createdBy:cn:searchString_2|nodeId:eq:1`  <br/>
> Filter by file `name` contains `searchString_1` OR creator info (`login`, `email`, `firstName`, `lastName`) contains `searchString_2` OR node ID is equal to `1`.<br/>
> <br/>
> ### Sorting<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields is supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **name**: Alias Name or File Name<br/>
> * **classification**: Classification ID (for files only):  <br/>
>     * 1 - public<br/>
>     * 2 - for internal use only<br/>
>     * 3 - confidential<br/>
>     * 4 - strictly confidential<br/>
> * **notifyCreator**: Notify creator on every download<br/>
> * **expireAt**: Expiration date<br/>
> * **createdAt**: Creation date<br/>
> * **createdBy**: Creator info<br/>
> <br/>
> ### Example:<br/>
> * `name:asc|expireAt:desc`  <br/>
> Sort by `name` ascending and by `expireAt` descending.

*Tags:* `shares`

#### Input Parameters
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Create new Download Share

> ### Functional Description:<br/>
> Create a new Download Share.<br/>
> <br/>
> ### Precondition:<br/>
> User with _"manage download share"_ permissions on target node.<br/>
> <br/>
> ### Effects:<br/>
> Download Share created.<br/>
> <br/>
> ### Further Information:<br/>
> <br/>
> * **Access password:** limited to **150** characters.<br/>
> * **Notes:** limited to **255** characters.<br/>
> * **Alias names:** limited to **150** characters.

*Tags:* `shares`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete Download Share

> ### Functional Description:<br/>
> Delete a Download Share.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> Download Share is deleted.<br/>
> <br/>
> ### Further Information:<br/>
> Only the Download Share is removed; the referenced file or container persists.

*Tags:* `shares`

#### Input Parameters
* `share_id` - _required_ - Share ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get Download Share

> ### Functional Description:  <br/>
> Retrieve detailed information about one Download Share.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `shares`

#### Input Parameters
* `share_id` - _required_ - Share ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get Download Share via QR Code

> ### Functional Description:  <br/>
> Retrieve detailed information about one Download Share.<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `shares`

#### Input Parameters
* `share_id` - _required_ - Share ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get Upload Shares

> ### Functional Description:  <br/>
> Retrieve a list of Upload Shares (aka Upload Accounts).<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filters<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE`  <br/>
> Multiple fields is supported.<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **name**  <br/>
>     Alias name  <br/>
>     OPERATOR: `cn` (Alias name contains value)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **createdBy**  <br/>
>     Creator info  <br/>
>     OPERATOR: `cn` (Creator info (`login`, `email`, `firstName`, `lastName`) contains value)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **accessKey**  <br/>
>     Share access key  <br/>
>     OPERATOR: `cn` (Share access key contains value)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **targetId**  <br/>
>     Target node (room, folder)  <br/>
>     **DEPRECATED** OPERATOR: `cn` (Target node contains value)  <br/>
>     **NEW** OPERATOR: `eq` (Target node equal value)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **userId**  <br/>
>     Creator user ID  <br/>
>     OPERATOR: `eq`  <br/>
>     VALUE: `Search user ID`<br/>
> <br/>
> ### Example:<br/>
> * `name:cn:searchString_1|createdBy:cn:searchString_2`  <br/>
> Filter by alias `name` contains `searchString_1` OR creator info (`login`, `email`, `firstName`, `lastName`) contains `searchString_2`.<br/>
> <br/>
> ### Sorting<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields is supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **name**: Alias name<br/>
> * **expireAt**: Expiration date<br/>
> * **notifyCreator**: Notify creator on every upload.<br/>
> * **createdAt**: Creation date<br/>
> * **createdBy**: Creator info<br/>
> <br/>
> ### Example:<br/>
> * `name:asc|expireAt:desc`  <br/>
> Sort by `name` ascending AND by `expireAt` descending.

*Tags:* `shares`

#### Input Parameters
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Create new Upload Share

> ### Functional Description:<br/>
> Create a new Upload Share (aka Upload Account).<br/>
> <br/>
> ### Precondition:<br/>
> User has _"manage upload share"_ permissions on target container.<br/>
> <br/>
> ### Effects:<br/>
> Upload Share is created.<br/>
> <br/>
> ### Further Information:<br/>
> <br/>
> * **Notes:** limited to **255** characters.<br/>
> * **Alias Names:** are limited to **150** characters.<br/>
> * **Send Mail:**:  <br/>
>     * If `sendMail` is set to `false`: `mailRecipients`; `mailSubject`; `mailBody` are **optional**.  <br/>
>     * If `sendMail` is set to `true`: `mailRecipients`; `mailSubject`; `mailBody` are **mandatory**.

*Tags:* `shares`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete Upload Share

> ### Functional Description:<br/>
> Delete an Upload Share (aka Upload Account).<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> Upload Share is deleted.<br/>
> <br/>
> ### Further Information:<br/>
> Only the Upload Share is removed; already uploaded files and the target container persist.

*Tags:* `shares`

#### Input Parameters
* `share_id` - _required_ - Share ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get Upload Share

> ### Functional Description:  <br/>
> Retrieve detailed information about one Upload Share (aka Upload Account).<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `shares`

#### Input Parameters
* `share_id` - _required_ - Share ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get Upload Share via QR Code

> ### Functional Description:  <br/>
> Retrieve detailed information about one Upload Share (aka Upload Account).<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `shares`

#### Input Parameters
* `share_id` - _required_ - Share ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get node assigned users with permissions

> ### Functional Description:  <br/>
> Retrieve a list of all nodes of type `room` and the room assignment users with permissions.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read audit log"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE`  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **nodeId**  <br/>
>     Node ID  <br/>
>     OPERATOR: `eq` (Node ID equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **nodeName**  <br/>
>     Node name (Login)  <br/>
>     OPERATOR: `cn|eq` (Node name contains value | equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **nodeParentId**  <br/>
>     Node parent ID  <br/>
>     OPERATOR: `eq` (Parent ID equal value; parent ID 0 is the root node.)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **userId**  <br/>
>     User ID  <br/>
>     OPERATOR: `eq` (User ID equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **userName**  <br/>
>     User name (Login)  <br/>
>     OPERATOR: `cn|eq` (User name contains value | equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **userFirstName**  <br/>
>     User first name  <br/>
>     OPERATOR: `cn|eq` (User first name contains value | equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **userLastName**  <br/>
>     User last name  <br/>
>     OPERATOR: `cn|eq` (User last name contains value | equal value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **permissionsManage**  <br/>
>     Filter the users that (don't) have manage right in this room  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **nodeIsEncrypted**  <br/>
>     Encrypted node filter  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> * **nodeHasRecycleBin**  <br/>
>     Recycle bin filter  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
>     <br/>
> * **nodeHasActivitiesLog**  <br/>
>     Activities log filter  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]`<br/>
> <br/>
> ### Logical grouping:<br/>
> Filtering according first three fields (`login`, `lastName`, `firstName`) is intrinsically processed by the API as logical _OR_.  <br/>
> In opposite, filtering according to is processed intrinsically as logical _AND_.<br/>
> <br/>
> ### Example:<br/>
> * `userName:cn:searchString_1|userFirstName:cn:searchString_2|nodeId:eq:2`  <br/>
> Filter by user login containing `searchString_1` OR first name containing `searchString_2` and node ID equal 2.<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **nodeId**: Node ID<br/>
> * **nodeName**: Node name<br/>
> * **nodeParentId**: Node parent ID<br/>
> * **nodeSize**: Node size<br/>
> * **nodeQuota**: Node quota<br/>
> <br/>
> ### Example:<br/>
> * `nodeName:asc`  <br/>
> Sort by `nodeName` ascending.

*Tags:* `syslog`

#### Input Parameters
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get system events

> ### Functional Description:  <br/>
> Retrieve eventlog (= audit log) events.<br/>
> <br/>
> ### Precondition:<br/>
> Role _"Log Auditor"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Output may be limited to a certain number of entries.  <br/>
> Please use filter criteria and paging.

*Tags:* `syslog`

#### Input Parameters
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `date_start` - _optional_ - Start date
e.g. 2015-12-31T23:59:00
* `date_end` - _optional_ - End date
e.g. 2015-12-31T23:59:00
* `type` - _optional_ - Operation ID
cf. `GET /eventlog/operations`
* `user_id` - _optional_ - User ID
* `status` - _optional_ - Operation status:
* 0 - Success
* 2 - Error
* `user_client` - _optional_ - User client
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get allowed Log Operations

> ### Functional Description:  <br/>
> Retrieve eventlog (= audit log) operation IDs and the associated log operation description.<br/>
> <br/>
> ### Precondition:<br/>
> Role _"Log Auditor"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `syslog`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Test active directory configuration

> ### Functional Description:  <br/>
> Test AD configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> DRACOON tries to establish a connection with the provided information.

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Test RADIUS server availability

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get active directory configuration

> ### Functional Description:  <br/>
> Retrieve a list of configured ADs.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Create active directory configuration

> ### Functional Description:<br/>
> Create a new AD configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_.<br/>
> <br/>
> ### Effects:<br/>
> New AD configuration created.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete active directory configuration

> ### Functional Description:<br/>
> Delete an existing AD configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_.<br/>
> <br/>
> ### Effects:<br/>
> AD configuration removed.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `ad_id` - _required_ - Active Directory ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get active directory configuration

> ### Functional Description:  <br/>
> Retrieve the configuration of a AD.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `ad_id` - _required_ - Active Directory ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Update active directory configuration

> ### Functional Description:  <br/>
> Update an existing AD configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_.<br/>
> <br/>
> ### Effects:<br/>
> AD configuration updated.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `ad_id` - _required_ - Active Directory ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get OpenID IDP configurations

> ### Functional Description:  <br/>
> Retrieve a list of configured OpenID Connect IDPs.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Create OpenID IDP configuration

> ### Functional Description:<br/>
> Create a new OpenID Connect IDP configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> New OpenID Connect IDP configuration is created.<br/>
> <br/>
> ### Further Information:<br/>
> See [http://openid.net/developers/specs](http://openid.net/developers/specs) for further information.

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Delete OpenID IDP configuration

> ### Functional Description:<br/>
> Delete an existing OpenID Connect IDP configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> OpenID Connect IDP configuration removed.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `idp_id` - _required_ - OpenID IDP configuration ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get OpenID IDP configuration

> ### Functional Description:  <br/>
> Retrieve an OpenID Connect IDP configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `idp_id` - _required_ - OpenID IDP configuration ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Update OpenID IDP configuration

> ### Functional Description:  <br/>
> Update an existing OpenID Connect IDP configuration.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> OpenID Connect IDP configuration is updated.<br/>
> <br/>
> ### Further Information:<br/>
> See [http://openid.net/developers/specs](http://openid.net/developers/specs) for further information.

*Tags:* `system`

#### Input Parameters
* `idp_id` - _required_ - OpenID IDP configuration ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Delete RADIUS Configuration

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get RADIUS Configuration

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Create RADIUS Configuration

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Update RADIUS Configuration

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get OAuth clients

> ### Functional Description:  <br/>
> Retrieve a list of configured OAuth clients.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Create OAuth client

> ### Functional Description:<br/>
> Create a new OAuth client.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> New OAuth client created.<br/>
> <br/>
> ### Further Information:  <br/>
> Client secret must have:  <br/>
> * at least 12 characters, at most 32 characters  <br/>
> * only lower case characters, upper case characters and digits  <br/>
> * at least 1 lower case character, 1 upper case character and 1 digit  <br/>
> <br/>
> The client secret is optional and will be generated if it is left empty.  <br/>
> <br/>
> Valid grant types are:  <br/>
> * **authorization_code**  <br/>
> * **implicit**  <br/>
> * **password**  <br/>
> * **client_credentials**  <br/>
> * **refresh_token**  <br/>
> <br/>
> Grant type `client_credentials` is actually not permitted!  <br/>
> <br/>
> Default access token validity: **8 hours**  <br/>
> Default refresh token validity: **30 days**

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Delete OAuth client

> ### Functional Description:<br/>
> Delete an existing OAuth client.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> OAuth client removed.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `client_id` - _required_ - OAuth client ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get OAuth client

> ### Functional Description:  <br/>
> Retrieve the configuration of an OAuth client.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `system`

#### Input Parameters
* `client_id` - _required_ - OAuth client ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Update OAuth client

> ### Functional Description:  <br/>
> Update an existing OAuth client.<br/>
> <br/>
> ### Precondition:<br/>
> Role _Config Manager_ of the Provider Customer.<br/>
> <br/>
> ### Effects:<br/>
> OAuth client updated.<br/>
> <br/>
> ### Further Information:  <br/>
> Client secret must have:  <br/>
> * at least 12 characters, at most 32 characters  <br/>
> * only lower case characters, upper case characters and digits  <br/>
> * at least 1 lower case character, 1 upper case character and 1 digit  <br/>
> <br/>
> The client secret is optional and will be generated if it is left empty.  <br/>
> <br/>
> Valid grant types are:  <br/>
> * **authorization_code**  <br/>
> * **implicit**  <br/>
> * **password**  <br/>
> * **client_credentials**  <br/>
> * **refresh_token**  <br/>
> <br/>
> Grant type `client_credentials` is actually not permitted!

*Tags:* `system`

#### Input Parameters
* `client_id` - _required_ - OAuth client ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get S3 Storage Configuration

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Create S3 Storage Configuration

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Update S3 Storage Configuration

*Tags:* `system`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Cancel file upload

> ### Functional Description:<br/>
> Cancel file upload.<br/>
> <br/>
> ### Precondition:<br/>
> Valid upload token.<br/>
> <br/>
> ### Effects:<br/>
> Upload canceled, token invalidated and all already transfered chunks removed.<br/>
> <br/>
> ### Further Information:<br/>
> It is recommended to notify the API about cancelled uploads if possible.

*Tags:* `uploads`

#### Input Parameters
* `token` - _required_ - Upload token

### Upload file by token

> ### Functional Description:  <br/>
> Upload a chunk of a file.<br/>
> <br/>
> ### Precondition:<br/>
> Valid upload token.<br/>
> <br/>
> ### Effects:<br/>
> Chunk uploaded.<br/>
> <br/>
> ### Further Information:<br/>
> Use this API if you cannot set custom headers during uploads.  <br/>
> Range requests are supported (please cf. [RCF 7233](https://tools.ietf.org/html/rfc7233) for details).

*Tags:* `uploads`

#### Input Parameters
* `token` - _required_ - Upload token
* `Content-Range` - _optional_ - Content-Range
e.g. "bytes 0-999/3980"
cf. [RFC 7233](https://tools.ietf.org/html/rfc7233)

### Complete file upload

> ### Functional Description:<br/>
> Finish uploading a file.<br/>
> <br/>
> ### Precondition:<br/>
> Valid upload token.<br/>
> <br/>
> ### Effects:<br/>
> File created.<br/>
> <br/>
> ### Further Information:<br/>
> The provided file name might be changed in accordance with the resolution strategy:<br/>
> <br/>
> * **autorename**: changes the file name and adds a number to avoid conflicts.<br/>
> * **overwrite**: deletes any old file with the same file name.<br/>
> * **fail**: returns an error; in this case, another `PUT` request with a different file name may be sent.<br/>
> <br/>
> Please ensure that all chunks have been transferred correctly before finishing the upload.<br/>
> <br/>
> ### 200 OK is not used by this API

*Tags:* `uploads`

#### Input Parameters
* `token` - _required_ - Upload token
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get user account info

> ### Functional Description:  <br/>
> Retrieves all information regarding the current user's account.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> Setting the query parameter `more_info` to `true`, causes the API to return more details e.g. the user's groups.

*Tags:* `user`

#### Input Parameters
* `more_info` - _optional_ - Get more info for this user
e.g. list of user groups
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Update user account

> ### Functional Description:  <br/>
> Update current user's account.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> User updated.<br/>
> <br/>
> ### Further Information:<br/>
> All input fields are limited to **150** characters.  <br/>
> Allowed characters: **All**  <br/>
> <br/>
> ### Authentication Method Options<br/>
> <br/>
> * **SQL**  <br/>
>     `none`<br/>
> <br/>
> * **Active Directory**  <br/>
>     (optional)  <br/>
>     key: `"ad_config_id"`  <br/>
>     value: "Active Directory configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "Active Directory user name according to auth setting `userFilter`"<br/>
> <br/>
> * **RADIUS**  <br/>
>     key: `"username"`  <br/>
>     value: "Radius user name"<br/>
> <br/>
> * **OpenID Connect**  <br/>
>     key: `"openid_config_id"`  <br/>
>     value: "OpenID Connect configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "OpenID Connect user name according to auth setting `mappingClaim`"

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get customer info

> ### Functional Description:  <br/>
> Lean API to get: <br/>
> * customer name<br/>
> * used / free space<br/>
> * used / avaliable<br/>
> * user account info<br/>
> <br/>
> of a customer.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Enable encryption for this customer

> ### Functional Description:  <br/>
> Activate client-side encryption for whole customer.<br/>
> <br/>
> ### Precondition:<br/>
> Only available for _"Config Managers"_.<br/>
> <br/>
> ### Effects:<br/>
> Client-side encryption is enabled.<br/>
> <br/>
> ### Further Information:<br/>
> Sets the ability for this customer to encrypt rooms.  <br/>
> Once enabled on customer level, it cannot be unset.  <br/>
> On activation, a emergency keypair must be set.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get customer keypair

> ### Functional Description:  <br/>
> Retrieve the customer's keypair (aka system emergency password).<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> The private key is password-based encrypted with `AES256` / `PBKDF2`.  <br/>
> Further details in crypto documentation.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Delete user keypair

> ### Functional Description:  <br/>
> Delete the user's keypair.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> This will also remove all file keys that were encrypted with the user's public key.  <br/>
> If the user had exclusive access to some files, those are removed as well since decrypting them became impossible.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get user keypair

> ### Functional Description:  <br/>
> Retrieve the user's keypair.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> The private key is password-based encrypted with `AES256` / `PBKDF2`.  <br/>
> Further details in crypto documentation.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Set user keypair

> ### Functional Description:  <br/>
> Set the user's keypair.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> The keypair is set.<br/>
> <br/>
> ### Further Information:<br/>
> Overwriting an existing keypair is not possible.  <br/>
> Please delete the existing keypair first.  <br/>
> The private key is password-based encrypted with `AES256` / `PBKDF2`.  <br/>
> Further details in crypto documentation.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Change user password

> ### Functional Description:<br/>
> Change the user's password.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> Password is changed.<br/>
> <br/>
> ### Further Information:<br/>
> Password security configuration applies.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Invalidate authentication token

> ### Functional Description:  <br/>
> Logout a user.<br/>
> <br/>
> ### Precondition:<br/>
> Valid authentication token.<br/>
> <br/>
> ### Effects:<br/>
> User is logged out, authentication token invalidated.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `user`

#### Input Parameters
* `everywhere` - _optional_ - Invalidate all tokens
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get OAuth client authorizations

> ### Functional Description:  <br/>
> Retrieve info about all OAuth client authorizations.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete OAuth authorization

> ### Functional Description:<br/>
> Delete authorizations of an OAuth client.<br/>
> <br/>
> ### Precondition:<br/>
> Valid auth token; valid client ID.<br/>
> <br/>
> ### Effects:<br/>
> Authorizations for OAuth client are revoked.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `user`

#### Input Parameters
* `client_id` - _required_ - OAuth client ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Ping

> ### Functional Description:<br/>
> Test connection to DRACOON Server (while authenticated).<br/>
> <br/>
> ### Precondition:<br/>
> None.<br/>
> <br/>
> ### Effects:<br/>
> `200 OK` with principal information is returned if successful.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `user`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get users

> ### Functional Description:  <br/>
> Get users entry point.  <br/>
> Returns a list of DRACOON users.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:  <br/>
> Authentication with `X-Sds-Auth-Token` required.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> Filter string syntax: `FIELD_NAME:OPERATOR:VALUE`  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **login**  <br/>
>     Login name  <br/>
>     OPERATOR: `cn` (User login name contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **firstName**  <br/>
>     First name  <br/>
>     OPERATOR: `cn` (User first name contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **lastName**  <br/>
>     Last name  <br/>
>     OPERATOR: `cn` (User last name contains value)  <br/>
>     VALUE: `Search string`<br/>
> <br/>
> * **lockStatus**  <br/>
>     Lock status:<br/>
>     * 0 - Locked<br/>
>     * 1 - Web access allowed<br/>
>     * 2 - Web and mobile access allowed  <br/>
>     <br/>
>     OPERATOR: `eq` (User lock status)  <br/>
>     VALUE: `[0|1|2]`.<br/>
> <br/>
> * **effectiveRoles**  <br/>
>     Filter users with _DIRECT_ or _DIRECT_ **AND** _EFFECTIVE_ roles  <br/>
>     * `false`: _DIRECT_ roles  <br/>
>     * `true`:  _DIRECT_ **AND** _EFFECTIVE_ roles  <br/>
> <br/>
>     > _DIRECT_ means: e.g. user gets role **directly** granted from someone with _grant permission_ right.  <br/>
>     _EFFECTIVE_ means: e.g. user gets role through **group membership**.  <br/>
> <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false]` (default: `false`)<br/>
> <br/>
> ### Logical grouping:<br/>
> Filtering according first three fields (`login`, `lastName`, `firstName`) is intrinsically processed by the API as logical _OR_.  <br/>
> In opposite, filtering according to last three field (lockStatus) is processed intrinsically as logical _AND_.<br/>
> <br/>
> ### Example:<br/>
> * `login:cn:searchString_1|firstName:cn:searchString_2|lockStatus:eq:2`  <br/>
> Filter by `login` contains `searchString_1` OR `firstName` contains `searchString_2` AND user are not locked.<br/>
> <br/>
> ### Sort<br/>
> <br/>
> Sort string syntax: `FIELD_NAME:ORDER`  <br/>
> Order can be `asc` or `desc`.  <br/>
> Multiple fields are supported.<br/>
> <br/>
> ### Sort fields:<br/>
> <br/>
> * **login**: Login name<br/>
> * **firstName**: First name<br/>
> * **lastName**: Last name<br/>
> * **gender**: Gender<br/>
> * **lockStatus**: User lock status<br/>
> * **lastLoginSuccessAt**: Last successful logon date<br/>
> * **expireAt**: Expiration date<br/>
> <br/>
> ### Example:<br/>
> * `firstName:asc|lastLoginSuccessAt:desc`  <br/>
> Sort by `firstName` ascending AND by `lastLoginSuccessAt` descending

*Tags:* `users`

#### Input Parameters
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `sort` - _optional_ - Sort string
* `include_attributes` - _optional_ - Include custom user attributes.
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Create user

> ### Functional Description:<br/>
> Create a new user.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> A new user is created.<br/>
> <br/>
> ### Further Information:<br/>
> <br/>
> * If a user should not expire, leave `expireAt` empty.<br/>
> * All input fields are limited to **150** characters<br/>
> * Allowed characters: **All**<br/>
> <br/>
> ### Authentication Method Options<br/>
> <br/>
> * **SQL**  <br/>
>     `none`<br/>
> <br/>
> * **Active Directory**  <br/>
>     (optional)  <br/>
>     key: `"ad_config_id"`  <br/>
>     value: "Active Directory configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "Active Directory user name according to auth setting `userFilter`"<br/>
> <br/>
> * **RADIUS**  <br/>
>     key: `"username"`  <br/>
>     value: "Radius user name"<br/>
> <br/>
> * **OpenID Connect**  <br/>
>     key: `"openid_config_id"`  <br/>
>     value: "OpenID Connect configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "OpenID Connect user name according to auth setting `mappingClaim`"

*Tags:* `users`

#### Input Parameters
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete user

> ### Functional Description:<br/>
> Delete a user.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"delete users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> User is deleted.<br/>
> <br/>
> ### Further Information:<br/>
> User cannot be deleted if he is the last room administrator.

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get user

> ### Functional Description:  <br/>
> Retrieve detailed information about single user.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Authentication Method Options<br/>
> <br/>
> * **SQL**  <br/>
>     `none`<br/>
> <br/>
> * **Active Directory**  <br/>
>     (optional)  <br/>
>     key: `"ad_config_id"`  <br/>
>     value: "Active Directory configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "Active Directory user name according to auth setting `userFilter`"<br/>
> <br/>
> * **RADIUS**  <br/>
>     key: `"username"`  <br/>
>     value: "Radius user name"<br/>
> <br/>
> * **OpenID Connect**  <br/>
>     key: `"openid_config_id"`  <br/>
>     value: "OpenID Connect configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "OpenID Connect user name according to auth setting `mappingClaim`"

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `effective_roles` - _optional_ - Effective roles
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Update user

> ### Functional Description:  <br/>
> Update the meta data of a user<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Meta data of a user is updated.<br/>
> <br/>
> ### Further Information:<br/>
> <br/>
> * If a user should not expire, leave `expireAt` empty.<br/>
> * All input fields are limited to **150** characters<br/>
> * Allowed characters: **All**<br/>
> <br/>
> ### Authentication Method Options<br/>
> <br/>
> * **SQL**  <br/>
>     `none`<br/>
> <br/>
> * **Active Directory**  <br/>
>     (optional)  <br/>
>     key: `"ad_config_id"`  <br/>
>     value: "Active Directory configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "Active Directory user name according to auth setting `userFilter`"<br/>
> <br/>
> * **RADIUS**  <br/>
>     key: `"username"`  <br/>
>     value: "Radius user name"<br/>
> <br/>
> * **OpenID Connect**  <br/>
>     key: `"openid_config_id"`  <br/>
>     value: "OpenID Connect configuration ID"  <br/>
>     <br/>
>     key: `"username"`  <br/>
>     value: "OpenID Connect user name according to auth setting `mappingClaim`"

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Get groups that user is a member of or/and can become a member

> ### Functional Description:  <br/>
> Retrieves a List of groups a user is member of and / or can become a member.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **name**  <br/>
>     Group name  <br/>
>     OPERATOR: `cn` (multiple values not allowed)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **isMember**  <br/>
>     Filter the groups which the user is or is not member of  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `true`)<br/>
> <br/>
> ### Example:<br/>
> * `is_member:eq:false|name:cn:searchString`  <br/>
> Get all groups that the user is not member of AND whose `name` is like `searchString`.

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get user roles

> ### Functional Description:  <br/>
> Retrieve a list of all roles and the role assignment rights of a user.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `X-Sds-Auth-Token` - _required_ - Authentication token

### Get rooms granted to the user or/and rooms that can be granted

> ### Functional Description:  <br/>
> Retrieves a list of rooms granted to the user and / or that can be granted.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"read users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> None.<br/>
> <br/>
> ### Further Information:<br/>
> None.<br/>
> <br/>
> ### Filter<br/>
> <br/>
> ### Filter fields:<br/>
> <br/>
> * **name**  <br/>
>     Room name  <br/>
>     OPERATOR: `cn` (multiple values not allowed)  <br/>
>     VALUE: `search string`<br/>
> <br/>
> * **isGranted**  <br/>
>     Filter the rooms which the user is or is not granted  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `true`)<br/>
> <br/>
> * **isLastAdmin**  <br/>
>     Filter the rooms which the user is last room administrator.  <br/>
>     Only with connect `isGranted:eq:true` possible.  <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true]`.<br/>
> <br/>
> * **effectivePerm**  <br/>
>     Filter rooms with _DIRECT_ or _DIRECT_ **AND** _EFFECTIVE_ permissions  <br/>
>     * `false`: _DIRECT_ permissions  <br/>
>     * `true`:  _DIRECT_ **AND** _EFFECTIVE_ permissions  <br/>
>     * `any`: _DIRECT_ **AND** _EFFECTIVE_ **AND** _OVER GROUP_ permissions  <br/>
>     <br/>
>     > _DIRECT_ means: e.g. room administrator grants read permissions to user **directly** on desired room.  <br/>
>     _EFFECTIVE_ means: e.g. user gets read permissions on desired room through **inheritance**.  <br/>
>     _OVER GROUP_ means: e.g. user gets read permissions on desired room through **group membership**.  <br/>
> <br/>
>     OPERATOR: `eq` (multiple values not allowed)  <br/>
>     VALUE: `[true|false|any]` (default: `false`)<br/>
> <br/>
> ### Examples:<br/>
> * `isGranted:eq:false|name:cn:searchString`  <br/>
> Get all rooms that the user is not granted AND whose `name` is like `searchString`.<br/>
> <br/>
> * `isGranted:eq:true|isLastAdmin:eq:true|name:cn:searchString`  <br/>
> Get all rooms that the user is granted AND is last admin AND whose `name` is like `searchString`.

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `offset` - _optional_ - Range offset
* `limit` - _optional_ - Range limit
* `filter` - _optional_ - Filter string
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Set custom user attributes

> ### Functional Description:  <br/>
> Set custom user attributes.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Custom user attributes gets set.<br/>
> <br/>
> ### Further Information:<br/>
> Batch function.  <br/>
> All existing user attributes will be deleted.  <br/>
> Allowed characters for keys are: `[a-zA-Z0-9_-]`  <br/>
> Characters are case-insensitive.

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Add or edit custom user attributes

> ### Functional Description:  <br/>
> Set custom user attributes.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Custom user attributes get added or edited.<br/>
> <br/>
> ### Further Information:<br/>
> Batch function.  <br/>
> If an entry exists before, it will be overwritten.  <br/>
> Allowed characters for keys are: `[a-zA-Z0-9_-]`  <br/>
> Characters are case-insensitive.

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `X-Sds-Auth-Token` - _required_ - Authentication token
* `X-Sds-Date-Format` - _optional_ - Date time format (cf. [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt)):
* LOCAL
* UTC
* OFFSET
* EPOCH

### Delete custom user attribute

> ### Functional Description:<br/>
> Delete custom user attribute.<br/>
> <br/>
> ### Precondition:<br/>
> Right _"change users"_ required.<br/>
> <br/>
> ### Effects:<br/>
> Custom user attribute gets deleted.<br/>
> <br/>
> ### Further Information:<br/>
> Allowed characters for keys are: `[a-zA-Z0-9_-]`  <br/>
> Characters are case-insensitive.

*Tags:* `users`

#### Input Parameters
* `user_id` - _required_ - User ID
* `key` - _required_ - Key
* `X-Sds-Auth-Token` - _required_ - Authentication token

## License

**flow**ground :- Telekom iPaaS / dracoon-team-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
