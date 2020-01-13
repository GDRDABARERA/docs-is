# Hosting Authentication Endpoint on a Different Server

The authenticationendpoint contains the authentication URLs used in
authentication flow. You can either host
the authenticationendpoint webapp on the WSO2 Identity Server, or choose
to host it on a separate server. You may want to host it separately for
the purpose of having custom theming and branding. This section
describes how you can host the authentication endpoint on a different
server outside the WSO2 Identity Server  (e.g., in a different Tomcat
Server).

##### Moving the authenticationendpoint from WSO2IS and hosting it on a separate web server

!!! tip "Before you begin"
    
   First, get a copy of
    `         <IS_HOME>/repository/deployment/server/webapps        `
    `         /authenticationendpoin.war        ` to
    `         <WebApp_HOME>/        ` and unzip it. Make sure to get the
    `         authenticationendpoin.war        ` after the WUM update and
    NOT the extracted `         authentication        `
    `         endpoint        ` in
    `         <IS_HOME>/repository/deployment/server/webapps/        `
    

1.  Copy the following .jar files from the
    `           <IS_HOME>/repository/components/plugins/ ` and ` IS_HOME>/lib/runtimes/cxf/        `
    directories to the
    `           <WebApp_HOME>/authenticationendpoint/WEB-INF/lib          `
    directory. Make sure below jar list will be coppied.

```    xml

      - XmlSchema_1.4.7.wso2v6.jar
	xercesImpl-2.8.1.wso2v2.jar
	wsdl4j_1.6.2.wso2v4.jar
	woodstox-core-asl-4.4.1.jar
	tomcat-servlet-api_9.0.22.wso2v1.jar
	tomcat-juli-9.0.22.jar
	tomcat-catalina-ha_9.0.22.wso2v1.jar
	taglibs-standard-impl-1.2.5.jar
	stax2-api-3.1.4.jar
	slf4j.api_1.7.21.jar
	rampart-core_1.6.1.wso2v40.jar
	pax-logging-api-1.11.0.jar
	org.wso2.securevault_1.1.3.jar
	org.wso2.carbon.utils_4.5.1.jar
	org.wso2.carbon.user.core_4.5.1.jar
	org.wso2.carbon.user.api_4.5.1.jar
	org.wso2.carbon.ui_4.5.1.jar
	org.wso2.carbon.securevault_4.5.1.jar
	org.wso2.carbon.registry.core_4.5.1.jar
	org.wso2.carbon.registry.api_4.5.1.jar
	org.wso2.carbon.queuing_4.5.1.jar
	org.wso2.carbon.identity.user.registration.stub_5.14.97.jar
	org.wso2.carbon.identity.template.mgt_5.14.97.jar
	org.wso2.carbon.identity.recovery.ui_1.3.15.jar
	org.wso2.carbon.identity.recovery.stub_1.3.15.jar
	org.wso2.carbon.identity.recovery_1.3.15.jar
	org.wso2.carbon.identity.mgt.ui_5.14.97.jar
	org.wso2.carbon.identity.mgt.stub_5.14.97.jar
	org.wso2.carbon.identity.mgt.endpoint.util_5.14.97.jar
	org.wso2.carbon.identity.mgt_5.14.97.jar
	org.wso2.carbon.identity.core_5.14.97.jar
	org.wso2.carbon.identity.base_5.14.97.jar
	org.wso2.carbon.identity.application.common_5.14.97.jar
	org.wso2.carbon.identity.application.authentication.endpoint.util_5.14.97.jar
	org.wso2.carbon.database.utils_2.0.10.jar
	org.wso2.carbon.crypto.api_1.1.2.jar
	org.wso2.carbon.core_4.5.1.jar
	org.wso2.carbon.bootstrap-4.5.1.jar
	org.wso2.carbon.base_4.5.1.jar
	org.eclipse.osgi.services_3.5.100.v20160504-1419.jar
	org.eclipse.osgi_3.14.0.v20190517-1309.jar
	org.eclipse.equinox.http.helper_1.1.0.wso2v1.jar
	opensaml_2.6.6.wso2v3.jar
	neethi_2.0.4.wso2v5.jar
	log4j-1.2.17.jar
	jstl_1.2.1.wso2v2.jar
	json_3.0.0.wso2v1.jar
	joda-time_2.9.4.wso2v1.jar
	jettison_1.3.4.wso2v1.jar
	jdbc-pool_9.0.16.wso2v1.jar
	jaxen-1.2.0.jar
	javax.ws.rs-api-2.1.1.jar
	javax.cache.wso2_4.5.1.jar
	httpcore_4.3.3.wso2v1.jar
	httpclient_4.3.6.wso2v2.jar
	hazelcast_3.12.2.wso2v1.jar
	geronimo-stax-api_1.0_spec-1.0.1.jar
	geronimo-jta_1.1_spec-1.1.jar
	geronimo-javamail_1.4_spec-1.7.1.jar
	geronimo-activation_1.1_spec-1.1.jar
	encoder-jsp-1.2.2.jar
	encoder_1.2.0.wso2v1.jar
	cxf-rt-transports-http-3.2.8.jar
	cxf-rt-rs-service-description-3.2.8.jar
	cxf-rt-rs-extension-search-3.2.8.jar
	cxf-rt-rs-extension-providers-3.2.8.jar
	cxf-rt-rs-client-3.2.8.jar
	cxf-rt-frontend-jaxrs-3.2.8.jar
	cxf-core-3.2.8.jar
	compass_2.0.1.wso2v2.jar
	commons-pool_1.5.6.wso2v1.jar
	commons-lang_2.6.0.wso2v1.jar
	commons-io_2.4.0.wso2v1.jar
	commons-httpclient_3.1.0.wso2v6.jar
	commons-fileupload_1.3.3.wso2v1.jar
	commons-dbcp_1.4.0.wso2v1.jar
	commons-collections4-4.0.jar
	commons-collections_3.2.2.wso2v1.jar
	commons-codec-1.4.jar
	commons-codec-1.4.0.wso2v1.jar
	commons-codec-1.12.jar
	commons-cli_1.2.0.wso2v1.jar
	com.google.gson_2.8.5.jar
	bcprov-jdk15on_1.60.0.wso2v1.jar
	axis2_1.6.1.wso2v38.jar
	axiom-api-1.2.11-wso2v16.jar
	axiom_1.2.11.wso2v16.jar
	ant_1.7.0.wso2v1.jar
	abdera_1.0.0.wso2v3.jar 
 ```

2.  Copy the following .jar files from the \<
    `          IS_HOME>/lib/runtimes/cxf/         ` directory to the
    `          <WebApp_HOME>/authenticationendpoint/WEB-INF/lib         `
    directory.  
    -   javax.ws.rs-api-2.0-m10.jar
    -   cxf-bundle-2.7.16.wso2v1.jar
    -   neethi-3.0.3.jar
    -   wsdl4j-1.6.3.jar
3.  Uncomment following section in
    `           <WebApp_HOME>/authenticationendpoint/WEB-INF/web.xml          `
    and point to identity server URLs.

    ``` xml
    ...   
    <context-param>
           <param-name>IdentityManagementEndpointContextURL</param-name>
    <param-value>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/accountrecoveryendpoint</param-value>
       </context-param>
        <context-param>
           <param-name>AccountRecoveryRESTEndpointURL</param-name>
         <param-value>https://localhost:9443/t/tenant-domain/api/identity/user/v0.9/</param-value>
       </context-param>
    ...
        <context-param>
            <param-name>IdentityServerEndpointContextURL</param-name>
            <param-value>https://localhost:9443</param-value>
        </context-param>
    ...
    ```

4.  Set the following configuration in
    `           <IS_HOME>/repository/conf/identity/application-authentication.properties          `
    file

    ```toml
    [authentication.endpoints] 
    login_url="https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/login.do"
    retry_url="https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/retry.do"
    request_missing_claims_url="https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/claims.do"
    ```

5.  Change the following configuration in
    `           <IS_HOME>/repository/conf/identity/identity.xml          `
    file to point to the authentication endpoint hosted outside the wso2
    server.

    ``` xml
        ...
        <OpenID>
            ...
            <OpenIDLoginUrl>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/openid_login.do</OpenIDLoginUrl>
            ...
        </OpenID>
        ...
        <OAuth>
            ...
            <OAuth2ConsentPage>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/oauth2_authz.do</OAuth2ConsentPage>
            <OAuth2ErrorPage>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/oauth2_error.do</OAuth2ErrorPage>
            <OIDCConsentPage>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/oauth2_consent.do</OIDCConsentPage>
            <OIDCLogoutConsentPage>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/oauth2_logout_consent.do</OIDCLogoutConsentPage>
            <OIDCLogoutPage>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/oauth2_logout.do</OIDCLogoutPage>
            ...
        </OAuth>
        ...
        <SSOService>
            ...  
            <DefaultLogoutEndpoint>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/samlsso_logout.do</DefaultLogoutEndpoint>
            <NotificationEndpoint>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/samlsso_notification.do</NotificationEndpoint>
            ...
        </SSOService>
        ...
        <PassiveSTS>
            ...
           <RetryURL>https://$WEB_SERVER_HOST:$WEB_SERVER_PORT/authenticationendpoint/retry.do</RetryUR>
            ...
        <PassiveSTS>
        ...
    ```

6.  Import the public certificate of the identity server to
    the javaca certs (or web-serverstruststore) of the JVM that
    the authenticationendpoint is running.

    ``` xml
    keytool -export -keystore $IS_HOME/repository/resources/security/wso2carbon.jks -alias wso2carbon -file wso2carbon.cer
    ```

    ``` xml
    keytool -import -alias wso2carbon -keystore  $WEB_APP_TRUSTSTORE -file wso2carbon.cer
    ```

7.  Import the public certificate of the Web\_server’s keystore to the
    Identity Server truststore.

    ``` xml
    keytool -export -keystore $WEB_APP_KEYSTORE -alias wso2carbon -file webserver.cer
    ```

    ``` xml
    keytool -import -alias <alias> -keystore  $IS_HOME/repository/resources/security/client-trustore.jks -file webserver.cer
    ```

##### Moving the accountrecoveryendpoint from WSO2IS and hosting it on a separate web server

This is an additional improvement which enables
hosting accountrecoveryendpoint.war also on a separate web server.

!!! tip "Before you begin"    
    Get a copy of
    `         <IS_HOME>/repository/deployment/server/webapps/accountrecoveryendpoint.war        `
    to `         <WebApp_HOME>/        ` and unzip it. Make sure to get the
    `         accountrecoveryendpoint.war        ` after the WUM update and
    not the extracted `         accountrecoveryendpoint        ` in
    `         <IS_HOME>/repository/deployment/server/webapps/        `
    

1.  In
    `           <WebApp_HOME>/accountrecoveryendpoint/WEB-INF/classes/RecoveryEndpointConfig.properties          `
    file, uncomment and change it to identity server.

    ``` xml
    identity.server.service.contextURL=https://localhost:9443/services/
    ```

2.  Uncomment and change the user portal reference in
    `           <WebApp_HOME>/accountrecoveryendpoint/WEB-INF/web.xml          `

    ``` xml
    <context-param>
            <param-name>UserPortalUrl</param-name>
            <param-value>https://localhost:9443/dashboard/index.jag</param-value>
    </context-param>
    ```

3.  Export the following paths.

    ``` xml
    export WEB_APP_HOME=/Users/userfoo/apache-tomcat-7.0.81/webapps
    export IS_HOME=/Users/userfoo/wso2is-5.6.0
    export WEB_APP_LIB=${WEB_APP_HOME}/accountrecoveryendpoint/WEB-INF/lib/
    ```

    Note: `           WEB_APP_HOME          ` and
    `           IS_HOME          ` paths are given as examples. You may
    have to change them according to your environment.

4.  Copy the following dependencies to
    `           <WebApp_HOME>/accountrecoveryendpoint/WEB-INF/lib  ` 
    from `<IS_HOME>/repository/components/plugins/ ` or  `<IS_HOME>/lib/runtimes/cxf/`. Make sure below .jars will be there.

 ``` xml
    
    XmlSchema-1.3.2.jar
	wsdl4j_1.6.2.wso2v4.jar
	org.wso2.securevault_1.1.3.jar
	org.wso2.carbon.utils_4.5.1.jar
	org.wso2.carbon.user.core_4.5.1.jar
	org.wso2.carbon.user.api_4.5.1.jar
	org.wso2.carbon.ui_4.5.1.jar
	org.wso2.carbon.tomcat.ext_4.5.1.jar
	org.wso2.carbon.idp.mgt.ui_5.14.97.jar
	org.wso2.carbon.idp.mgt.stub_5.14.97.jar
	org.wso2.carbon.idp.mgt_5.14.97.jar
	org.wso2.carbon.identity.user.registration.stub_5.14.97.jar
	org.wso2.carbon.identity.recovery.ui_1.3.15.jar
	org.wso2.carbon.identity.recovery.stub_1.3.15.jar
	org.wso2.carbon.identity.recovery_1.3.15.jar
	org.wso2.carbon.identity.mgt.ui_5.14.97.jar
	org.wso2.carbon.identity.mgt.stub_5.14.97.jar
	org.wso2.carbon.identity.mgt.endpoint.util_5.14.97.jar
	org.wso2.carbon.identity.mgt_5.14.97.jar
	org.wso2.carbon.identity.core_5.14.97.jar
	org.wso2.carbon.identity.base_5.14.97.jar
	org.wso2.carbon.identity.application.mgt.ui_5.14.97.jar
	org.wso2.carbon.identity.application.mgt.stub_5.14.97.jar
	org.wso2.carbon.identity.application.mgt_5.14.97.jar
	org.wso2.carbon.identity.application.common_5.14.97.jar
	org.wso2.carbon.identity.application.authentication.endpoint.util_5.14.97.jar
	org.wso2.carbon.base_4.5.1.jar
	org.eclipse.equinox.jsp.jasper_1.1.200.v20190214-1948.jar
	org.apache.commons.commons-codec_1.12.0.jar
	opensaml_2.6.6.wso2v3.jar
	neethi_2.0.4.wso2v5.jar
	mimepull-1.9.3.jar
	jsr311-api-1.0.jar
	json_3.0.0.wso2v1.jar
	jettison_1.3.4.wso2v1.jar
	jersey-multipart-1.19.1.jar
	jersey-core-1.19.1.jar
	jersey-client-1.19.1.jar
	javax.ws.rs-api-2.1.1.jar
	javax.mail-api-1.6.0.jar
	javax.cache.wso2_4.5.1.jar
	jackson-module-jaxb-annotations-2.9.9.jar
	jackson-jaxrs-json-provider-2.9.9.jar
	jackson-jaxrs-base-2.9.9.jar
	jackson-databind-2.9.9.3.jar
	jackson-core-2.9.9.jar
	jackson-annotations-2.9.9.jar
	httpcore_4.3.3.wso2v1.jar
	httpclient_4.3.6.wso2v2.jar
	encoder_1.2.0.wso2v1.jar
	cxf-rt-transports-http-3.2.8.jar
	cxf-rt-rs-service-description-3.2.8.jar
	cxf-rt-rs-extension-search-3.2.8.jar
	cxf-rt-rs-extension-providers-3.2.8.jar
	cxf-rt-rs-client-3.2.8.jar
	cxf-rt-frontend-jaxrs-3.2.8.jar
	cxf-core-3.2.8.jar
	commons-logging-1.2.jar
	commons-lang3_3.4.0.wso2v1.jar
	commons-lang_2.6.0.wso2v1.jar
	commons-httpclient-3.1.jar
	commons-collections_3.2.2.wso2v1.jar
	com.google.gson_2.8.5.jar
	axis2_1.6.1.wso2v38.jar
	axiom-impl-1.2.11.jar
	axiom-api-1.2.11-wso2v6.jar
	axiom-api-1.2.11-wso2v16.jar
	axiom-1.2.11-wso2v16.jar
	axiom_1.2.11.wso2v16.jar

 ```

 !!! note
    
   Make sure the WebApp container server (of endpoint apps) is
        running with SSL enabled.
    
   e.g., if tomcat enabled the https connector, add the following to `catalina.sh `         ` .
    
   ``` xml
        JAVA_OPTS="$JAVA_OPTS -Djavax.net.ssl.keyStore=$WEB_SERVER_KEYSTORE -Djavax.net.ssl.keyStorePassword=$password"
        JAVA_OPTS="$JAVA_OPTS -Djavax.net.ssl.trustStore=$WEBSERVER_TRUSTORE -Djavax.net.ssl.trustStorePassword=$password"
   ```
    

##### Running the sample
<a name="step2"></a>

1.  Download and install WSO2 IS and apache-tomcat into your local
    machine. Let’s consider IS installation as
    `           <IS_HOME>          ` and tomcat installation as
    `           <TOMCAT_HOME>          `

2.  Get the sample setup scripts from the following location:
    `                     https://github.com/ayshsandu/samples/tree/master/is_samples/is_5.6.0/hosting-endpoints                   `
    .

3.  Open `           <TOMCAT_HOME>/conf/server.xml          ` file and
    enable the https connector on 8443 port.
    ``` xml
    <Connector port="8443" protocol="org.apache.coyote.http11.Http11NioProtocol"
              maxThreads="150" SSLEnabled="true" scheme="https" secure="true"
              clientAuth="want" sslProtocol="TLS"
              sslEnabledProtocols="TLSv1,TLSv1.1,TLSv1.2"      keystoreFile="$IS_HOME/repository/resources/security/wso2carbon.jks"
    keystorePass="wso2carbon" truststoreFile="$IS_HOME/repository/resources/security/client-truststore.jks" truststorePass="wso2carbon"/>
    ```

    !!! note

        For this sample, we configured the same keystore and truststore in
        WSO2IS as the keystore and truststore in tomcat. In an actual
        environment, you may create a new keystore and truststore for tomcat
        and point to it. When using separate keystores and truststores, you
        need to import tomcat keystore’s public cert in to:
    
        `           <          `
        `           IS_HOME>/repository/resources/security/client-truststore.jks          `
        and, public cert of `           <          `
        `           IS_HOME>/repository/resources/security/wso2carbon.jks          `
        into tomcat’s truststore.
    

4.  Open `           <TOMCAT_HOME>/bin/catalina.sh          ` and add
    following JAVA\_OPTS.

 ``` xml
    JAVA_OPTS="$JAVA_OPTS --Djavax.net.ssl.keyStore=$IS_HOME/repository/resources/security/wso2carbon.jks -Djavax.net.ssl.keyStorePassword=wso2carbon"
    JAVA_OPTS="$JAVA_OPTS -Djavax.net.ssl.trustStore=$IS_HOME/repository/resources/security/client-truststore.jks -Djavax.net.ssl.trustStorePassword=wso2carbon"
 ```

5.  Run `          setup-authentication.sh         ` obtained from [step
    2](#step2) and
    follow the instructions.

6.  Once the script is complete, then the authentication endpoint is set
    up in the given `          <TOMCAT_HOME>/webapps         ` location.

7.  Uncomment following section in
    `           <TOMCAT_HOME>/webapps/authenticationendpoint/WEB-INF/web.xml          `
    file and point to identity server URLs.

  ``` xml
    ...  
    <context-param>
            <param-name>IdentityManagementEndpointContextURL</param-name>
    <param-value>https://localhost:9443/accountrecoveryendpoint</param-value>
        </context-param>
        <context-param>
            <param-name>AccountRecoveryRESTEndpointURL</param-name>
            <param-value>https://localhost:9443/t/tenant-domain/api/identity/user/v0.9/</param-value>
        </context-param>
    ...
        <context-param>
            <param-name>IdentityServerEndpointContextURL</param-name>
            <param-value>https://localhost:9443</param-value>
        </context-param>
    ...
  ```

8.  Change the following configuration in
    `           <IS_HOME>/repository/conf/identity/application-authentication.xml   `       `
    file.

  ```toml    
    [authentication.endpoints] 
    login_url="https://localhost:8443/authenticationendpoint/login.do"
    retry_url="https://localhost:8443/authenticationendpoint/retry.do"
    request_missing_claims_url="https://localhost:8443/authenticationendpoint/claims.do"
  ```

9.  Change the following configuration in
    `           <IS_HOME>/repository/conf/identity/identity.xml          `
    file to point to the authentication endpoint hosted outside the wso2
    server.

  ```toml
    [oauth.endpoints]
    oauth2_consent_page= "https://localhost:8443/authenticationendpoint/oauth2_authz.do"
    oauth2_error_page= "https://localhost:8443/authenticationendpoint/oauth2_error.do"
    oidc_consent_page= "https://localhost:8443/authenticationendpoint/oauth2_consent.do"
    oidc_logout_consent_page= "https://localhost:8443/authenticationendpoint/oauth2_logout_consent.do"
    oidc_logout_page= "https://localhost:8443/authenticationendpoint/oauth2_logout.do"

    [saml.endpoints] 
    logout= "https://localhost:8443/authenticationendpoint/samlsso_logout.do"
    notification= "https://localhost:8443/authenticationendpoint/samlsso_notification.do"

    [passive_sts.endpoints] 
    retry= "https://localhost:8443/authenticationendpoint/retry.do"
  ```
    
10. Start both Identity Server and tomcat and access
    `                       https://localhost:9443/dashboard  `  
     Now you can see that the authentication is redirected to:
    `                       https://localhost:8443/authenticationendpoint/login.do   `                  `

    Now let’s take out account recovery endpoint into the external
    Tomcat server as well.

11. Run `          setup-accountrecovery.sh         ` obtained from
    [step 2](#step2) and
    follow the instructions.

12. Change the following section in
    `           <TOMCAT_HOME>/webapps/authenticationendpoint/WEB-INF/web.xml          `
    file and point to
    `           IdentityManagementEndpointContextURL          `
    into tomcat URL.

  ``` xml
    ... 
    <context-param>
            <param-name>IdentityManagementEndpointContextURL</param-name>
    <param-value>https://localhost:8443/accountrecoveryendpoint</param-value>
        </context-param>
    ...
  ```

13. In
    `           <TOMCAT_HOME>/accountrecoveryendpoint/WEB-INF/classes/RecoveryEndpointConfig.properties          `
    file, uncomment and change it to identity server.

   ``` xml
    identity.server.service.contextURL=https://localhost:9443/services
   ```

14. Uncomment and change the user portal reference in
    `           <TOMCAT_HOME>/account          `
    `           recovery          `
    `           endpoint/WEB-INF/web.xml          `

  ``` xml
    ...
        <context-param>
            <param-name>UserPortalUrl</param-name>
            <param-value>https://localhost:9443/dashboard/index.jag</param-value>
        </context-param>
    ...
  ```

15. After restarting the server double check the `User self registration callback URL regex` peoperty in the Resident IDP configurations of the super tenant or tenants. Make sure it will be `https://localhost:8443/authenticationendpoint/login.do` as shown in the below image. Do the same for recovery as well.
