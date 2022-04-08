# Keycloak

Keycloak is an Open Source Identity and Access Management and provides user federation, strong authentication, user management, fine-grained authorization, and more.

**Single-Sign On**  
Users authenticate with Keycloak rather than individual applications. This means that applications don't have to deal with login forms, authenticating users, and storing users. Once logged-in to Keycloak, users don't have to login again to access a different application. This also applied to logout.

**User Federation**  
Keycloak has built-in support to connect to existing LDAP or Active Directory servers.

**Identity Brokering and Social Login**  
Enabling login with social networks is easy to add through the admin console. Keycloak can also authenticate users with existing OpenID Connect or SAML 2.0 Identity Providers.

## Links

- [Keycloak Getting Started](https://www.keycloak.org/getting-started/getting-started-zip)
- [Keycloak Documentation](https://www.keycloak.org/documentation)
- [Keycloak Docker Image](https://github.com/keycloak/keycloak-containers/blob/16.1.0/server/README.md)
- [Install Keycloak on CentOS 7 with MySQL backend](https://www.pimwiddershoven.nl/entry/install-keycloak-on-centos-7-with-mysql-backend)

Local standalone installation

- [Keycloak Admin Console](http://localhost:8080/auth/admin)
- [Keycloak Account Console for realm test](http://localhost:8080/auth/realms/test/account)

Tutorials

- [Stian Thorgersen: Keycloak Intro](https://www.youtube.com/watch?v=duawSV69LDI)
- [A deep dive into Keycloak](https://github.com/stianst/keycloak-containers-demo)

## Installation

Keycloak installation options are

- bare metal
- Docker
- Podman
- Kubernetes
- Openshift
- Kubernetes Operator
- OpenShift Operator

### Windows / Linux

- OpenJDK 1.8 or newer installed.
- download the zip-file for the latest version from the Keycloak website
- extract the zip-file
- open a terminal in the keycloak directory and run the following command

  > On Linux: `bin/standalone.sh`  
  > On Windows: `bin/standalone.bat`

### Default ports

| Protocol                 | Port |
| ------------------------ | ---- |
| ajp                      | 8009 |
| http                     | 8080 |
| https                    | 8443 |
| management-http          | 9990 |
| management-https         | 9993 |
| txn-recovery-environment | 4712 |
| txn-status-manager       | 4713 |

In standalone mode they can be changed in

> \standalone\configuration\standalone.xml

### Important directories

| Directory               | Contains                                                                       |
| ----------------------- | ------------------------------------------------------------------------------ |
| bin/                    | various scripts to boot or manage the server                                   |
| domain/                 | configuration files and working directory when running in domain mode          |
| modules/                | Java libraries                                                                 |
| standalone/             | configuration files and working directory when running in standalone mode      |
| standalone/deployments/ | extensions to Keycloak                                                         |
| themes/                 | html, style sheets, JavaScript files, and images used to display any UI screen |

### Next steps

- open `http://localhost:8080/auth` and create an admin user
- login to the admin console and login
- create a realm
- create a user
- create credentilas for the user
- login to account console

A realm allows creating isolated groups of applications and users.  
The default realm master is dedicated to manage Keycloak and should not be used for own applications.

## Using standalone mode

Standalone operating mode is only useful when you want to run exactly one Keycloak server instance.
It is only useful for testing and not recommended in production.

### Booting in standalone mode

The standalone Boot scripts for running the server in standalone mode are located in the bin/ directory

> On Linux: `bin/standalone.sh`  
> On Windows: `bin\standalone.bat`

### Standalone configuration

The configuration file in standalone operation mode is

> ./standalone/configuration/standalone.xml

This file is used to configure infrastructure (specific to the underlying application server of Keycloak) and non-infrastructure (specific to Keycloak components) level things. Any changes to this file while the server is running will not take effect and may even be overwritten by the server. Stop the server or use the command line scripting or the web console of WildFly.

### Using standalone clustered mode

Standalone clustered operation mode applies when you want to run Keycloak within a cluster.  
This mode requires that you have a copy of the Keycloak distribution on each machine where you want to run a server instance. This mode can be very easy to deploy initially. For a large cluster, this mode can become time consuming and error prone. To make a configuration change, you modify each distribution on each machine.

### Standalone clustered configuration

The configuration file in standalone clustered operation mode is

> ./standalone/configuration/standalone-ha.xml

The distribution has a mostly pre-configured app server configuration file for running within a cluster. It has all the specific infrastructure settings for networking, databases, caches, and discovery.

Things needed for this configuration

- configuring a shared database connection
- a load balancer in front of the cluster

### Configuration in standalone clustered mode

The configuration file in standalone clustered operation mode is

> ./standalone/configuration/standalone-ha.xml

### Booting in standalone clustered mode

The standalone Boot scripts for running the server in standalone mode are located in the bin/ directory

> On Linux: `/bin/standalone.sh --server-config=standalone-ha.xml`  
> On Windows: `\bin\standalone.bat --server-config=standalone-ha.xml`

## Server Administration

Keycloak is a single sign on solution for web apps and REST-based web services.

The goal of Keycloak is to make security simple so that it is easy for application developers to secure the apps and services. Security features that developers normally have to write for themselves are provided out of the box and are easily tailorable to the individual requirements of your organization.

Keycloak provides customizable user interfaces for login, registration, administration, and account management.

You can also use Keycloak as an integration platform to hook it into existing LDAP and Active Directory servers.

You can also delegate authentication to third party identity providers like Facebook and Google.

Keycloak is a separate server that you manage on your network. Applications are configured to point to and be secured by this server.

Browser applications redirect a user’s browser from the application to the Keycloak authentication server where they enter their credentials. This redirection is important because users are completely isolated from applications and applications never see a user’s credentials.

Applications are given an identity token or assertion that is cryptographically signed.

These tokens can have identity information like username, address, email, and other profile data.

They can also hold permission data so that applications can make authorization decisions.

These tokens can also be used to make secure invocations on REST-based services.

### Core concepts and terms

| Term                         | Definition                                                                                                                                                                                                                                                                                                                                                                 |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| users                        | Users are entities that are able to log in. They can have attributes associated with themselves like email, username, address, and birth day. They can be assigned group membership and have specific roles assigned to them.                                                                                                                                              |
| authentication               | The process of identifying and validating a user.                                                                                                                                                                                                                                                                                                                          |
| authorization                | The process of granting access to a user.                                                                                                                                                                                                                                                                                                                                  |
| credentials                  | Credentials are pieces of data used to verify the identity of a user. Examples are passwords, one-time-passwords, digital certificates or even fingerprints.                                                                                                                                                                                                               |
| roles                        | Roles identify a type or category of user. Admin, user, manager or employee are typical roles. Applications often assign access and permissions to specific roles rather than individual users.                                                                                                                                                                            |
| user role mapping            | A user role mapping defines a mapping between a role and a user. A user can be associated with zero or more roles. This role mapping information can be encapsulated into tokens and assertions so that applications can decide access permissions on various resources they manage.                                                                                       |
| composite roles              | A composite role is a role that can be associated with other roles. For example if a user is mapped to the superuser role they also inherit the sales-admin and order-entry-admin roles.                                                                                                                                                                                   |
| groups                       | Groups manage groups of users. Attributes can be defined for a group. You can map roles to a group as well. Users that become members of a group inherit the attributes and role mappings that group defines.                                                                                                                                                              |
| realms                       | A realm manages a set of users, credentials, roles, and groups. A user belongs to and logs into a realm. Realms are isolated from one another and can only manage and authenticate the users that they control.                                                                                                                                                            |
| clients                      | Clients are entities that can request Keycloak to authenticate a user. Most often, clients are applications and services. Clients can also be entities that just want to request identity information or an access token so that they can securely invoke other services on the network that are secured by Keycloak.                                                      |
| client adapters              | Client adapters are plugins that you install into the application environment to be able to communicate and be secured by Keycloak. Keycloak has a number of adapters for different platforms. There are also third-party adapters.                                                                                                                                        |
| consent                      | Consent is when you as an admin want a user to give permission to a client before that client can participate in the authentication process. After a user provides their credentials, Keycloak will pop up a screen identifying the client requesting a login and what identity information is requested of the user. User can decide whether or not to grant the request. |
| client scopes                | When a client is registered, you must define protocol mappers and role scope mappings for that client. It is often useful to store a client scope, to make creating new clients easier by sharing some common settings.                                                                                                                                                    |
| client role                  | Clients can define roles that are specific to them, i.e.basically a role namespace dedicated to the client.                                                                                                                                                                                                                                                                |
| identity token               | A token that provides identity information about the user.                                                                                                                                                                                                                                                                                                                 |
| access token                 | A token that can be provided as part of an HTTP request that grants access to the service being invoked on.                                                                                                                                                                                                                                                                |
| assertion                    | Information about a user. This usually pertains to an XML blob that is included in a SAML authentication response that provided identity metadata about an authenticated user.                                                                                                                                                                                             |
| service account              | Each client has a built-in service account which allows it to obtain an access token.                                                                                                                                                                                                                                                                                      |
| direct grant                 | A way for a client to obtain an access token on behalf of a user via a REST invocation.                                                                                                                                                                                                                                                                                    |
| protocol mappers             | For each client you can tailor what claims and assertions are stored in the OIDC token or SAML assertion.                                                                                                                                                                                                                                                                  |
| session                      | When a user logs in, a session is created to manage the login session. A session contains information like when the user logged in and what applications have participated within single-sign on during that session.                                                                                                                                                      |
| user federation provider     | Keycloak can store and manage users. Often, companies already have LDAP or Active Directory services that store user and credential information. You can point Keycloak to validate credentials from those external stores and pull in identity information.                                                                                                               |
| identity provider            | An identity provider (IDP) is a service that can authenticate a user. Keycloak is an IDP.                                                                                                                                                                                                                                                                                  |
| identity provider federation | Keycloak can be configured to delegate authentication to one or more IDPs. Social login via Facebook or Google+ is an example of identity provider federation.                                                                                                                                                                                                             |
| identity provider mappers    | When doing IDP federation you can map incoming tokens and assertions to user and session attributes. This helps you propagate identity information from the external IDP to your client requesting authentication.                                                                                                                                                         |
| required actions             | Required actions are actions a user must perform during the authentication process, for instance a monthly password change. A user will not be able to complete the authentication process until these actions are complete.                                                                                                                                               |
| authentication flows         | Authentication flows are work flows a user must perform when interacting with certain aspects of the system. A login flow can define what credential types are required. A registration flow defines what profile information a user must enter and whether something like reCAPTCHA must be used to filter out bots.                                                      |
| events                       | Events are audit streams that admins can view and hook into.                                                                                                                                                                                                                                                                                                               |
| themes                       | Every screen provided by Keycloak is backed by a theme. Themes define HTML templates and stylesheets and can be overridden as needed.                                                                                                                                                                                                                                      |
