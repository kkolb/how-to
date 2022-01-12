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
- extracting the zip-file
- open a terminal in the keycloak directory and run the following command
  > On Linux: `bin/standalone.sh`
  > On Windows: `bin/standalone.bat`
