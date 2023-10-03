This example demonstrates how to use [Express](http://expressjs.com/) 4.x and
[Passport](http://passportjs.org/) to authenticate users via [SAML 2.0](http://saml.xml.org/saml-specifications).
Use this example as a starting point for your own web applications.

## Instructions

To install this example on your computer, clone the repository and install
dependencies.

```bash
$ git clone git@github.com:passport/express-4.x-saml2-example.git
$ cd express-4.x-saml2-example
$ npm install
```

## Configure Keycloak

Here is how to run a local Keycloak server:

```shell
docker run \
  -p 8080:8080 \
  -e KEYCLOAK_ADMIN=admin \
  -e KEYCLOAK_ADMIN_PASSWORD=admin \
  quay.io/keycloak/keycloak:22.0.3 \
  start-dev
```

Then follow the instructions in https://www.keycloak.org/getting-started/getting-started-docker to set up a new realm
(`my-realm`).

Note that the above instructs you to create an OIDC app, but we want a SAML app. So, please amend the above instructions 
create a SAML app instead. You will also have to provide the following Configuration settings:

* Under the `Settings` tab:
  * Client ID: `example`
  * Root URL: `http://localhost:3000/`
  * Home URL: `http://localhost:3000/`
  * Valid redirect URIs: `*` ‼️This is not safe for prod ‼️
* Under the `Keys` tab:
  * Client signature required: `Off`
  

