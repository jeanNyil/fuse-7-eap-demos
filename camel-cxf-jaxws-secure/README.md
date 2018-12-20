Camel Secure CXF JAX-WS
------------------------

This example demonstrates using the camel-cxf component with Red Hat Fuse on EAP to produce and consume JAX-WS web
services secured by an Elytron Security Domain. Elytron is a new security framework available since _Red Hat JBoss EAP 7.1_.

In this example, a Camel route takes a message payload from a direct endpoint and passes it on to a CXF producer
endpoint. The producer uses the payload to pass arguments to a CXF JAX-WS web service that is secured by _BASIC HTTP
authentication_.

Moreover, all the exchanged SOAP messages are *signed and encrypted* according to the _X509 signature and encryption
WS-security policy_.

Prerequisites
-------------

* _Apache Maven 3.5+_
* _Red Hat JBoss EAP 7.1_ server with _Red Hat Fuse 7.2_ installed

Running the example
-------------------

To run the example.

1. Use the add-user script to create a new server application user and group

    For Linux:

    `${JBOSS_HOME}/bin/add-user.sh -a -u testUser -p testPassword1+ -g testRole`

    For Windows:

   `%JBOSS_HOME%\bin\add-user.bat -a -u testUser -p testPassword1+ -g testRole`

2. Start the application server in standalone mode:

    For Linux:

    `${JBOSS_HOME}/bin/standalone.sh -c standalone-full.xml`

    For Windows:

    `%JBOSS_HOME%\bin\standalone.bat -c standalone-full.xml`

3. Set the Security Domain using a JBoss CLI script.

    For Linux:

    `${JBOSS_HOME}/bin/jboss-cli.sh --connect --file=configure-basic-security.cli`

    For Windows:

    `%JBOSS_HOME%\bin\jboss-cli.bat --connect --file=configure-basic-security.cli`

4. Study `jboss-web-xml` and `web.xml` files in `webapp/WEB-INF` directory of this project. They
set the application security domain, security roles and constraints.

5. Build and deploy the project `mvn install -Pdeploy`

6. Browse to _http://*<jboss\_eap\_host>*:8080/example-camel-cxf-jaxws-secure/_

You should see a page titled 'Send A Greeting'. This UI enables us to interact with the test 'greeting' web service which will have also been started.

Testing Camel Secure CXF JAX-WS
-------------------------------

Web UI
------

Browse to _http://*<jboss\_eap\_host>*:8080/example-camel-cxf-jaxws-secure/_.

From the 'Send A Greeting' web form, enter a 'message' and 'name' into the text fields and press the 'send' button. You'll then see the information you entered combined to display a greeting on the UI.

`CamelCxfWsServlet` handles the POST request from the web UI. It retrieves the message and name form parameter values and constructs an object array. This object array will be the message payload that is sent to the `direct:start` endpoint. A `ProducerTemplate` sends the message payload to Camel. `The direct:start` endpoint passes the object array to a `cxf:bean` web service producer. The web service response is used by `CamelCxfWsServlet` to display the greeting on the web UI.

The full Camel route can be seen in [_*cxfws-security-camel-context.xml*_](src/main/webapp/WEB-INF/cxfws-security-camel-context.xml).

SOAP-UI
-------

The service WSDL is available at _http://*<jboss\_eap\_host>*:8080/webservices/greeting-security-basic?wsdl_.

There is a single service operation named `greet` which takes 2 _String_ parameters named `message` and `name`. Invoking the web service will return a response where these values have been concatenated together.

![Rejected request without basic auth](../images/soapUIwithoutBasicAuth_KO.png)
![Rejected request with basic auth but no X509 signature/encryption](../images/soapUIwithBasicAuthAndNoX509Sign_KO.png)


## Undeploy

1. To undeploy the example run `mvn clean -Pdeploy`.

2. Unconfigure the example tls security configuration:

    For Linux:

    `${JBOSS_HOME}/bin/jboss-cli.sh --connect --file=remove-basic-security.cli`

    For Windows:

    `%JBOSS_HOME%\bin\jboss-cli.bat --connect --file=remove-basic-security.cli`
