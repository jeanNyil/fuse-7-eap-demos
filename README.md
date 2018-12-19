## Red Hat Fuse on EAP Examples

This directory contains a suite of useful modules to demonstrate various features of the Red Hat Fuse on EAP.
Their aim is to provide small, specific and working examples that can be used for reference in your own projects.
* [camel-cxf-jaxws-crypto](camel-cxf-jaxws-crypto)
* [camel-cxf-jaxws-secure](camel-cxf-jaxws-secure)

![Fuse 7 on JBoss EAP HawtIO](images/fuse-7-eap-hawtio.png)

### :raised_hands: NOTE :raised_hands:
All the examples are based on the [_The WildFly-Camel Examples_](https://github.com/wildfly-extras/wildfly-camel-examples.git).

### :warning: ATTENTION

You have to adapt the `wildfly-maven-plugin according to your _JBoss EAP_ environment

### Prerequisites

The examples require a running application server with Red Hat Fuse on EAP installed. Refer to the Red Hat Fuse on EAP installation documentation for how to do this.

### Running Examples

Each example aims to be interactive to help you learn how to get started with the Red Hat Fuse on EAP. Each example
can be accessed by changing into the example source directory, building the project `mvn clean install` and then deploying
to a running application server `mvn install -Pdeploy`.

Examples can be undeployed from a running application server by running `mvn clean -Pdeploy`.

### :warning: TODO
* Add Camel PGP message crypto in the [camel-cxf-jaxws-crypto](camel-cxf-jaxws-crypto) module
* Complete the following in the [camel-cxf-jaxws-secure](camel-cxf-jaxws-secure) module
  * The direct route must enforce X509 Signature/encrypt WS-Security policy as expected by the CXFConsumer route
  * Resolve the following issue encountered on the CXFConsumer route (Fuse 7.2/EAP 7.1.5): `org.apache.wss4j.common.ext.WSPasswordCallback cannot be cast to org.apache.wss4j.common.ext.WSPasswordCallback`
    * Complete stack trace:
```
2018-12-19 18:59:51,844 INFO  [org.apache.cxf.services.GreetingServiceService.greetingPort.greeting] (default task-6) Inbound Message
----------------------------
ID: 10
Address: http://fuse-eap-01.lab.com:8080/webservices/greeting-security-basic
Encoding: UTF-8
Http-Method: POST
Content-Type: text/xml;charset=UTF-8
Headers: {accept-encoding=[gzip,deflate], Authorization=[Basic dGVzdFVzZXI6dGVzdFBhc3N3b3JkMSs=], connection=[Keep-Alive], Content-Length=[8613], content-type=[text/xml;charset=UTF-8], Host=[fuse-eap-01.lab.com:8080], SOAPAction=["urn:greet"], User-Agent=[Apache-HttpClient/4.1.1 (java 1.5)]}
Payload: <soapenv:Envelope xmlns:jax="http://jaxws.cxf.examples.camel.wildfly.org/" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
   <soapenv:Header><wsse:Security xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"><ds:Signature Id="SIG-3E07C705D64E678A48154524239124728" xmlns:ds="http://www.w3.org/2000/09/xmldsig#"><ds:SignedInfo><ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"><ec:InclusiveNamespaces PrefixList="jax soapenv" xmlns:ec="http://www.w3.org/2001/10/xml-exc-c14n#"/></ds:CanonicalizationMethod><ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/><ds:Reference URI="#id-3E07C705D64E678A48154524239124327"><ds:Transforms><ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"><ec:InclusiveNamespaces PrefixList="jax" xmlns:ec="http://www.w3.org/2001/10/xml-exc-c14n#"/></ds:Transform></ds:Transforms><ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/><ds:DigestValue>5ldlnAVu9snU9PMzBh50k0HIuv4=</ds:DigestValue></ds:Reference></ds:SignedInfo><ds:SignatureValue>eqLr3Z3MGTH32ewRg3ty1SbjOAZtk25zDifWAY+05IP4XmWqwke0Hsn9ZxD6boJtEUIIitZNhGDq
FsJu7LOA06H3dpNsEKVg1o74qPJ2i+Uzn4qoxs0C+sbuZpFv7q1SIWuK1UhXAeqmwXfgu2RRydJ7
+kJ2N1zsD0+UYVvuzx6VO0w9ATwqkYsQW0Mdqp1UkZkQfuUvNFT38B7uY3xd1wGHzDbYYELdF7VT
bV88xTpFxw9DU//VEcgFFRRuLDkPxm0P0ypCs1QWPEPX2jjIskupSwOWPn2Jzk8FEG7yliHEdPFK
+7fPnUelJ4dbexx2xB1VUaGQZ183YzNgVQ5f81jBv9ajXQohuNS4FnP6ZWbXEFwzTpiwRh7nglXg
wc+YtwcT3FrCAktGf87Ky4w0HFh6XVSeoG02vYq+QaieRwaFb6g+rqxDK5lqYc+p2jCaOf5nZVBl
KggY2AvxHBUcTeh4wtzQZzoyfLSPd9Uo6dcDIP+h44os4S5jenRi/qN/oSFLPKDqzr+W9SJLOtV7
JmiumPixMt47SOxt5kgfe5H1nhbsZ4oLyvTF3CIF4g0J8iI2OQrOTtUoVIxzKltKnQvPTAVvxmpy
NOHGbViFrY215F7sr1jB/PH6lSC0PNau2O0zPFyZTnvmF/oKEEg4hKfCK+Ky4elk8bJG52jl/0U=</ds:SignatureValue><ds:KeyInfo Id="KI-3E07C705D64E678A48154524239124225"><wsse:SecurityTokenReference wsu:Id="STR-3E07C705D64E678A48154524239124326"><wsse:KeyIdentifier EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3">MIIE1TCCAr2gAwIBAgIEFOfroTANBgkqhkiG9w0BAQsFADAbMRkwFwYDVQQDExB3cy14NTA5c2lnbmF0dXJlMB4XDTE4MTIxOTE1Mjc1N1oXDTE5MDMxOTE1Mjc1N1owGzEZMBcGA1UEAxMQd3MteDUwOXNpZ25hdHVyZTCCAiIwDQYJKoZIhvcNAQEBBQADggIPADCCAgoCggIBAKmFE4fSQJSMbgnHah+hIUIuCH3e1IidjbgEhA94gL0nQT7BAA/49L75POHHgZPsITBzf1VmZQJtfJ1mUrRGlX760WQb4LMpQT/hvC/N1MkOhbfxOLi/hzhW3UwTKrj02eMled+GNi+D1pNSBDVZuV+0HZVxUPNKDsAPVSxidzDsH5e/CBK5XlUS/NfTKFFegApZCtJdodNddI/cP/UGyChTSg/Ll+TtfLTM88IFpaFgSJEDSV0+q7HZy6wiGSepg/yM8yH5SOCJaUoZPX5dhj/XdmWtxbbJBi7U3gAOkdgi59FikZ6fWRvjaVMskrDlEQ8daejejz85fUIaAMPmDJPE7TtQbEMKoA8lRrHp6TGjIvo4DGclYa/auHS0ObKl9m36/w75YOEkJmGTAwVQ/z5BFT2W7bUii1xei70sysLmY6TZxszfSlizH2Nhq5Aq4C9MoGpgkAdMC4ZKWa8TshumC0Ikw5VZxJ4gOUvux+tJd9uAE/ZNGL3Tz7QViZuidU02wxKnSYyLBNX22AweSzZnU/1FSYHTB/OEoO0SkMHgZeBdtyotvs4Mvxa2pMjm/EZ+2ofT50AKHsweWSBKgMJc2Pvs2RHlbAiCn2pF9SZEhRV8rOah8Vy7r5r3gLfMgl3SawSjbuzz3C4TA/afuvoe+WJP+v7Rf7bAJG5qMFSRAgMBAAGjITAfMB0GA1UdDgQWBBRp4VnP98cFMbk/p/W4voHhJmVOXTANBgkqhkiG9w0BAQsFAAOCAgEAe1YkTPzf1E292mzC7SiXUlN0PoVxhtktBsOOwOtMF+aG3xMh4mFdc+MgUFd/Tl34PgRLg7T9YUzYipkbmFtV35HPoVagNWbMag8lnB6eiedJt3CHKarRjalfQ7nXPVdl4LDMnM9dlISLYIn3/zocTu/25TvvSXtMKKfyHY8XZVBGvtdseNiclV4Sqkg+uE/SHAsFJBePL5elM+Lrgs5nQrzs0EM6oUNHBI5d/glRVZESi2zgrUuwnSCRWLM5vJPTYpUGv62NLxrp/+5ejUqTm6K3+NvZosGwBxb6sPqZ+UJ+59OMB0HlGIlO+bcwLRm/nUDkhFwFAwj+SFwaUi8FEg0D8sALp6o5MdAQ1WI5nMEQ5733AtWJMsRrj25Wb/2VjQ9NqtQmtCVMKjL/8Eqc8eI4/Pn0WrJPWNUZ3oF5lb0wrgi3y2WmumymQ6FSBBIZjnlFkn66ikxl5fvnQCF4JhpOFF3Z7NHyT/YkFlfbCXMXLX2WEy9HwUsD9Ffc3jXFg02IDcguooglyM3GXBPHtRl/W4TNRuLUTI5gswweX/AIOBKi9GJ4NLLY31xbwEDeOgQYfL5EllWw1YIYQ9sud7pVOMsNNa6ndExCzgXh6DtM+Ga5BN/Z10/MGByQQt0Lr5ATQUUuzakKKMA9NbKBIR2O/vT4cGDvcZSedU1OOq0=</wsse:KeyIdentifier></wsse:SecurityTokenReference></ds:KeyInfo></ds:Signature><xenc:EncryptedKey Id="EK-3E07C705D64E678A48154524239122322" xmlns:xenc="http://www.w3.org/2001/04/xmlenc#"><xenc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/><ds:KeyInfo xmlns:ds="http://www.w3.org/2000/09/xmldsig#"><wsse:SecurityTokenReference><wsse:KeyIdentifier EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3">MIIE1TCCAr2gAwIBAgIEFOfroTANBgkqhkiG9w0BAQsFADAbMRkwFwYDVQQDExB3cy14NTA5c2lnbmF0dXJlMB4XDTE4MTIxOTE1Mjc1N1oXDTE5MDMxOTE1Mjc1N1owGzEZMBcGA1UEAxMQd3MteDUwOXNpZ25hdHVyZTCCAiIwDQYJKoZIhvcNAQEBBQADggIPADCCAgoCggIBAKmFE4fSQJSMbgnHah+hIUIuCH3e1IidjbgEhA94gL0nQT7BAA/49L75POHHgZPsITBzf1VmZQJtfJ1mUrRGlX760WQb4LMpQT/hvC/N1MkOhbfxOLi/hzhW3UwTKrj02eMled+GNi+D1pNSBDVZuV+0HZVxUPNKDsAPVSxidzDsH5e/CBK5XlUS/NfTKFFegApZCtJdodNddI/cP/UGyChTSg/Ll+TtfLTM88IFpaFgSJEDSV0+q7HZy6wiGSepg/yM8yH5SOCJaUoZPX5dhj/XdmWtxbbJBi7U3gAOkdgi59FikZ6fWRvjaVMskrDlEQ8daejejz85fUIaAMPmDJPE7TtQbEMKoA8lRrHp6TGjIvo4DGclYa/auHS0ObKl9m36/w75YOEkJmGTAwVQ/z5BFT2W7bUii1xei70sysLmY6TZxszfSlizH2Nhq5Aq4C9MoGpgkAdMC4ZKWa8TshumC0Ikw5VZxJ4gOUvux+tJd9uAE/ZNGL3Tz7QViZuidU02wxKnSYyLBNX22AweSzZnU/1FSYHTB/OEoO0SkMHgZeBdtyotvs4Mvxa2pMjm/EZ+2ofT50AKHsweWSBKgMJc2Pvs2RHlbAiCn2pF9SZEhRV8rOah8Vy7r5r3gLfMgl3SawSjbuzz3C4TA/afuvoe+WJP+v7Rf7bAJG5qMFSRAgMBAAGjITAfMB0GA1UdDgQWBBRp4VnP98cFMbk/p/W4voHhJmVOXTANBgkqhkiG9w0BAQsFAAOCAgEAe1YkTPzf1E292mzC7SiXUlN0PoVxhtktBsOOwOtMF+aG3xMh4mFdc+MgUFd/Tl34PgRLg7T9YUzYipkbmFtV35HPoVagNWbMag8lnB6eiedJt3CHKarRjalfQ7nXPVdl4LDMnM9dlISLYIn3/zocTu/25TvvSXtMKKfyHY8XZVBGvtdseNiclV4Sqkg+uE/SHAsFJBePL5elM+Lrgs5nQrzs0EM6oUNHBI5d/glRVZESi2zgrUuwnSCRWLM5vJPTYpUGv62NLxrp/+5ejUqTm6K3+NvZosGwBxb6sPqZ+UJ+59OMB0HlGIlO+bcwLRm/nUDkhFwFAwj+SFwaUi8FEg0D8sALp6o5MdAQ1WI5nMEQ5733AtWJMsRrj25Wb/2VjQ9NqtQmtCVMKjL/8Eqc8eI4/Pn0WrJPWNUZ3oF5lb0wrgi3y2WmumymQ6FSBBIZjnlFkn66ikxl5fvnQCF4JhpOFF3Z7NHyT/YkFlfbCXMXLX2WEy9HwUsD9Ffc3jXFg02IDcguooglyM3GXBPHtRl/W4TNRuLUTI5gswweX/AIOBKi9GJ4NLLY31xbwEDeOgQYfL5EllWw1YIYQ9sud7pVOMsNNa6ndExCzgXh6DtM+Ga5BN/Z10/MGByQQt0Lr5ATQUUuzakKKMA9NbKBIR2O/vT4cGDvcZSedU1OOq0=</wsse:KeyIdentifier></wsse:SecurityTokenReference></ds:KeyInfo><xenc:CipherData><xenc:CipherValue>In7+vwf7GgaYatB42hyZtEGTi7k9t0v0G5s/Ye0e1RAdeWzi5Uh2/c27OeInMInm7pC22IvWCIDRVl6A6nvqO+9Tp4pq1oSYJd7mxt/Rvoi1WXQKXJjQA1nXAbM8T3Sz8aAVr9Dzm72dD0cKf6mz0/ysdooFPqV2eOCyY3xFMjLsNI1LsrtjDVwCvKp50EFwNrenc3OTteU78uT0+0yL6YHanGxNq514J7vvBLuryUkGww/ELjfkp5q2vx72V4/VldLczCppr/5hMQiO0LDztLOTVDxGRXFTsPdZOBRyoKA4S2DtNV5sspvv1iFEAVwtQZeADt63Uxq2AWuft8YXqFLyLF0nwAVgb+J646XiVQ1IrRmHUF+wcoCICd0gECjcXMjgah3oQFZ5LXu+9TxCxHw5tTd4Sf9vUeyA/ykoUSUyT465Ijdy+9JU07ruRZQVVG+TFTOCslQhxtyz9bTxfz8i2ZPlz+agXz372Rr5C0e3DrQ7nJYm4C7sqqyg2H7tdakiJ5cuEXK+0AIwXHuUlgwcADrCGQlvW5gp7Wxre1rqKDxSnhxFHcnuTJVHKtYrxmJBEq02BiPF8BdS4PBue7inn99jYUB2xnRuqTJTPUrb2MSt4GiMfCiTSC0igUxN0Wze5uGIOsUhJOv7MRd/gCuucL+gy2R7vWNKTjpvaB0=</xenc:CipherValue></xenc:CipherData><xenc:ReferenceList><xenc:DataReference URI="#ED-3E07C705D64E678A48154524239122523"/></xenc:ReferenceList></xenc:EncryptedKey></wsse:Security></soapenv:Header>
   <soapenv:Body wsu:Id="id-3E07C705D64E678A48154524239124327" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"><xenc:EncryptedData Id="ED-3E07C705D64E678A48154524239122523" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:xenc="http://www.w3.org/2001/04/xmlenc#"><xenc:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes128-cbc"/><ds:KeyInfo xmlns:ds="http://www.w3.org/2000/09/xmldsig#"><wsse:SecurityTokenReference wsse11:TokenType="http://docs.oasis-open.org/wss/oasis-wss-soap-message-security-1.1#EncryptedKey" xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd" xmlns:wsse11="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"><wsse:Reference URI="#EK-3E07C705D64E678A48154524239122322"/></wsse:SecurityTokenReference></ds:KeyInfo><xenc:CipherData><xenc:CipherValue>vn75znZP7dzBBI4CLZQFvlnUYddKTDXi8TYQUo8ryJ3a9ys00VjGU8Ru4MINOBSu6sT4MyYrCg4JQoxXpK72jmvvTJDhZ1liN5ccWJs4eh5jv9eciJFYtwSPy6/nvG19TpU7lNjy5mHnnmw5rfIIcfXe9uv3tEc+5ZBsgpMJej5XrIIXU1sOLJphNRXnZm8cPykqD7aTNY6wav5DFeEUVdLtnRsd1a31SIXZ6xnPDfluTaNE61lILfRA3ijFTrESnlnAJPRB3w3VNonPzhkSP/lHZoVcZWfCqP+e8WlKiqVo/gnJdL0ZAORdOCfqwaZPZkNjmRSHkLOowCet3LgtnV0TYVq0gG5Abw8pbXv9jqWBs7W/Z6Qz5YiOOcozISpKcwjWhwewYIlfE88qsesM+YLYmraGui204mEk/wNiw9MiIdMm9Y6YwLeoa9WPGtxtS74svjwvgaMnjvrzEZFcsg==</xenc:CipherValue></xenc:CipherData></xenc:EncryptedData></soapenv:Body>
</soapenv:Envelope>
--------------------------------------
2018-12-19 18:59:52,248 WARNING [org.apache.cxf.phase.PhaseInterceptorChain] (default task-6) Interceptor for {http://jaxws.cxf.examples.camel.wildfly.org/}GreetingServiceService#{http://jaxws.cxf.examples.camel.wildfly.org/}greet has thrown exception, unwinding now: java.lang.ClassCastException: org.apache.wss4j.common.ext.WSPasswordCallback cannot be cast to org.apache.wss4j.common.ext.WSPasswordCallback
	at org.wildfly.camel.examples.cxf.jaxws.ServiceKeystorePasswordCallback.handle(ServiceKeystorePasswordCallback.java:24)
	at org.apache.cxf.ws.security.wss4j.TokenStoreCallbackHandler.handle(TokenStoreCallbackHandler.java:64)
	at org.apache.wss4j.common.crypto.Merlin.getPassword(Merlin.java:1516)
	at org.apache.wss4j.common.crypto.Merlin.getPrivateKey(Merlin.java:655)
	at org.apache.wss4j.dom.processor.EncryptedKeyProcessor.getPrivateKey(EncryptedKeyProcessor.java:272)
	at org.apache.wss4j.dom.processor.EncryptedKeyProcessor.handleToken(EncryptedKeyProcessor.java:232)
	at org.apache.wss4j.dom.processor.EncryptedKeyProcessor.handleToken(EncryptedKeyProcessor.java:92)
	at org.apache.wss4j.dom.engine.WSSecurityEngine.processSecurityHeader(WSSecurityEngine.java:345)
	at org.apache.cxf.ws.security.wss4j.WSS4JInInterceptor.handleMessageInternal(WSS4JInInterceptor.java:276)
	at org.apache.cxf.ws.security.wss4j.WSS4JInInterceptor.handleMessage(WSS4JInInterceptor.java:172)
	at org.apache.cxf.ws.security.wss4j.WSS4JInInterceptor.handleMessage(WSS4JInInterceptor.java:81)
	at org.apache.cxf.phase.PhaseInterceptorChain.doIntercept(PhaseInterceptorChain.java:309)
	at org.apache.cxf.transport.ChainInitiationObserver.onMessage(ChainInitiationObserver.java:121)
	at org.apache.cxf.transport.http.AbstractHTTPDestination.invoke(AbstractHTTPDestination.java:267)
	at org.apache.cxf.transport.undertow.UndertowHTTPDestination.service(UndertowHTTPDestination.java:179)
	at org.wildfly.extension.camel.service.CamelEndpointDeployerService$EndpointServlet.service(CamelEndpointDeployerService.java:505)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:790)
	at io.undertow.servlet.handlers.ServletHandler.handleRequest(ServletHandler.java:74)
	at io.undertow.servlet.handlers.security.ServletSecurityRoleHandler.handleRequest(ServletSecurityRoleHandler.java:62)
	at io.undertow.servlet.handlers.ServletChain$1.handleRequest(ServletChain.java:65)
	at io.undertow.servlet.handlers.ServletDispatchingHandler.handleRequest(ServletDispatchingHandler.java:36)
	at org.wildfly.elytron.web.undertow.server.ElytronRunAsHandler.lambda$handleRequest$1(ElytronRunAsHandler.java:68)
	at org.wildfly.security.auth.server.FlexibleIdentityAssociation.runAsFunctionEx(FlexibleIdentityAssociation.java:101)
	at org.wildfly.security.auth.server.Scoped.runAsFunctionEx(Scoped.java:150)
	at org.wildfly.security.auth.server.Scoped.runAs(Scoped.java:62)
	at org.wildfly.elytron.web.undertow.server.ElytronRunAsHandler.handleRequest(ElytronRunAsHandler.java:67)
	at io.undertow.servlet.handlers.security.SSLInformationAssociationHandler.handleRequest(SSLInformationAssociationHandler.java:131)
	at io.undertow.servlet.handlers.security.ServletAuthenticationCallHandler.handleRequest(ServletAuthenticationCallHandler.java:57)
	at io.undertow.server.handlers.DisableCacheHandler.handleRequest(DisableCacheHandler.java:33)
	at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)
	at io.undertow.security.handlers.AuthenticationConstraintHandler.handleRequest(AuthenticationConstraintHandler.java:53)
	at io.undertow.security.handlers.AbstractConfidentialityHandler.handleRequest(AbstractConfidentialityHandler.java:46)
	at io.undertow.servlet.handlers.security.ServletConfidentialityConstraintHandler.handleRequest(ServletConfidentialityConstraintHandler.java:64)
	at io.undertow.servlet.handlers.security.ServletSecurityConstraintHandler.handleRequest(ServletSecurityConstraintHandler.java:59)
	at io.undertow.security.handlers.AbstractSecurityContextAssociationHandler.handleRequest(AbstractSecurityContextAssociationHandler.java:43)
	at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)
	at org.wildfly.extension.undertow.security.jacc.JACCContextIdHandler.handleRequest(JACCContextIdHandler.java:61)
	at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)
	at org.wildfly.extension.undertow.deployment.GlobalRequestControllerHandler.handleRequest(GlobalRequestControllerHandler.java:68)
	at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)
	at io.undertow.servlet.handlers.ServletInitialHandler.handleFirstRequest(ServletInitialHandler.java:292)
	at io.undertow.servlet.handlers.ServletInitialHandler.access$100(ServletInitialHandler.java:81)
	at io.undertow.servlet.handlers.ServletInitialHandler$2.call(ServletInitialHandler.java:138)
	at io.undertow.servlet.handlers.ServletInitialHandler$2.call(ServletInitialHandler.java:135)
	at io.undertow.servlet.core.ServletRequestContextThreadSetupAction$1.call(ServletRequestContextThreadSetupAction.java:48)
	at io.undertow.servlet.core.ContextClassLoaderSetupAction$1.call(ContextClassLoaderSetupAction.java:43)
	at org.wildfly.extension.undertow.deployment.UndertowDeploymentInfoService$UndertowThreadSetupAction.lambda$create$0(UndertowDeploymentInfoService.java:1501)
	at org.wildfly.extension.undertow.deployment.UndertowDeploymentInfoService$UndertowThreadSetupAction.lambda$create$0(UndertowDeploymentInfoService.java:1501)
	at org.wildfly.extension.undertow.deployment.UndertowDeploymentInfoService$UndertowThreadSetupAction.lambda$create$0(UndertowDeploymentInfoService.java:1501)
	at org.wildfly.extension.undertow.deployment.UndertowDeploymentInfoService$UndertowThreadSetupAction.lambda$create$0(UndertowDeploymentInfoService.java:1501)
	at io.undertow.servlet.handlers.ServletInitialHandler.dispatchRequest(ServletInitialHandler.java:272)
	at io.undertow.servlet.handlers.ServletInitialHandler.access$000(ServletInitialHandler.java:81)
	at io.undertow.servlet.handlers.ServletInitialHandler$1.handleRequest(ServletInitialHandler.java:104)
	at io.undertow.server.Connectors.executeRootHandler(Connectors.java:330)
	at io.undertow.server.HttpServerExchange$1.run(HttpServerExchange.java:812)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
	at java.lang.Thread.run(Thread.java:748)

2018-12-19 18:59:52,251 INFO  [org.apache.cxf.services.GreetingServiceService.greetingPort.greeting] (default task-6) Outbound Message
---------------------------
ID: 10
Response-Code: 500
Encoding: UTF-8
Content-Type: text/xml
Headers: {}
Payload: <soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"><soap:Body><soap:Fault><faultcode>soap:Server</faultcode><faultstring>org.apache.wss4j.common.ext.WSPasswordCallback cannot be cast to org.apache.wss4j.common.ext.WSPasswordCallback</faultstring></soap:Fault></soap:Body></soap:Envelope>
--------------------------------------
```


