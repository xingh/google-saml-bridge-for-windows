# Introduction #

Windows SAML Bridge 2.8 has the following three new features:

1. SAML Bridge support for POST binding

2. Configurable username format during SAML authentication

3. Configurable authorization trust duration value (in Web.config)


## 1. SAML Bridge Post binding ##

### Ensure Post.aspx is properly configured for security ###

Make sure Post.aspx is protected in the deployed SAML Bridge on IIS.  Inside IIS Manager, click on Post.aspx in the SAML Bridge site, click on the File Security tab, and make sure the following options are set:

Deselect "Enable anonymous access".
Select "Integrated Windows authentication" for Authenticated Access.

### Configure SAML Bridge to use the private key for Post Binding ###

Post Binding requires a public key and private key pair to be used to encrypt and decrypt the response message from the SAML IDP. The SAML IDP uses the private key to encrypt the message, and the GSA uses the public key to decrypt it.



SAML Bridge will look for the certificate located in server key store. You can follow the standard process of enabling HTTPS for IIS web site to create a key request, generate a certificate from your CA, and upload to IIS server where the SAML Bridge is installed. You don't have to enable HTTPS for the web site.



To locate the certificate on the server that you created or select one which you'd like to use, go to Start menu, select Run, type in mmc to bring up the management console. Select the menu

File, select Add/Remove Snap-in, click on Add,  select Certificates, click on Add. This will bring up a wizard which lets you choose the account that would manage the certificates. Choose Computer Account, and then click on Next; select Local Computer, and then click on Finish. Now it turns to the previous dialog box. Click on Close, and then OK to return to the main window. Drill down on the certificates tree on the left navigation bar. Expands on Personal node where the certificate on IIS is usually stored. Locate the certificate, and double click on the certificate. This will bring up the properties window for the certificate. Select Details tab, find the attribute Friendly name, identify add the name to the certificate\_friendly\_name entry in web.config of SAML Bridge. Also note down the value of the Subject attribute for granting access to the certificate (see below).

### Grant SAML Bridge access to the certificate ###

In order for SAML Bridge to load the certificate which contains the private key from the key store, the Application Pool Identity that runs the SAML Bridge must have appropriate rights to access the certificate. In order to check that, you can download the WinnHttpCertCfg tool.

To show the accounts that have access to this certificate:

winhttpcertcfg -l -c LOCAL\_MACHINE\My -s any\_word\_in\_the\_subject\_attribute\_of\_the\_certificate

To grant to access to the certificate to account "Network Service"

winhttpcertcfg -g -c LOCAL\_MACHINE\My -s any\_word\_in\_the\_subject\_attribute\_of\_the\_certificate -a "Network Service"

### Get public key ###

You need to copy the public key in text format and paste it into the SAML configuration in GSA's Admin Console. You can get the base64 encoded text from the certificate if it's in PEM format. If you don't have the certificate in PEM format, you need to use some tools to convert from other formats to PEM format. If the certificate is also used for HTTPS, you can use FireFox. Open FireFox browser, go to the website where the certificate is used for HTTPS. You should see a lock icon on the status bar. A Certificate Viewer window will pop up. Click on View Certificate, selectDetails tab, click on Export, save the certificate in PEM format.


### Configure GSA to use SAML Bridge with Post Binding ###

In GSA Admin console, go to Serving->Universal Login Auth Mechanisms, select SAML tab, Enter a value in Mechanism Name. Enter a value in IDP Entity ID. You need to enter the same value in the Web.config in SAML Bridge. Enter http://<URL to the saml bridge>/Post.aspx in the Login URL field. Open the saved certificate file in a text editor. Copy the content and paste it in the Public Key of IDP field. Click Save.

## 2. Configurable username format during SAML authentication ##

SAML bridge 2.8 provides facility to configure the username format returned by the SAML authentication which matches your authorization mechanism on the GSA.

In web.config, see the following parameter:

<!-- available format: user@domain, user, domain\user-->


&lt;add key="subject\_format" value="user@domain"/&gt;



You can provide either of  user@domain, user or domain\user as a value for the key "subject\_format".

## 3. Configurable authorization trust duration value ##

In web.config, see the following parameter:

<!-- trust duration in seconds - the SAML Bridge machine and the GSA must be synced to the same NTP server-->



&lt;add key="trust\_duration" value="300"/&gt;



By default, the value is 300 seconds (5 min). You may change this to optimal value depending on your setup.