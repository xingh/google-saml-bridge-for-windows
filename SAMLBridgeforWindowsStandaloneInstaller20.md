# Introduction #

The Google SAML bridge for Windows Installer is used to install SAML bridge 2.0 on non-SharePoint servers.

The SAML bridge component is also bundled into the Google Search Appliance Resource Kit for SharePoint installer, but it can be installed only on servers having SharePoint installation. This blocks the users who want to use SAML-bridge component alone from the Google Search Appliance Resource Kit for SharePoint installer, and without the SharePoint installation.


# Pre-requisites #

  * Windows Server 2003 Enterprise server/Windows Server 2008 Enterprise server.
  * Microsoft .Net Framework 2.0.
  * IIS 6.0/IIS 7.0.


# Features #

The Google SAML bridge for Windows 2.0 bundles the 2.0 version of the SAML bridge.

SAML bridge for Windows allows users to gain seamless access to content that resides on file systems, web servers, or Microsoft Office SharePoint servers.

# Installation #

The Google SAML bridge for Windows does not contain a check for the existence of SharePoint installation on target servers, and hence can be installed on non-SharePoint servers. Prior to the installation, please refer the section [#Pre-requisites](#Pre-requisites.md)

In case of any issues, please refer the [Troubleshooting guide for the saml bridge](http://code.google.com/p/google-saml-bridge-for-windows/wiki/SAMLBridgeFAQsTroubleshooting)

### Installing the SAML Bridge ###

You can install the SAML Bridge on any IIS server that meets the prerequisites described above.

To install the SAML Bridge:

1. Start a web browser and navigate to the http://code.google.com/p/google-saml-bridge-for-windows/downloads/list

2. Download the SAML bridge for Windows 2.0 package for your operating system (x86 or x64).

3. Unzip the package.

4. Locate the installer, which is the file with the extension msi.

5. Double-click the installer file. The Welcome screen is displayed.

6. Click Next.

7. Accept the License Agreement and click Next.

8. Click Install.

9. Enter a valid unused port number. The installer creates a web site in IIS with the port number you enter.

10. Enter the value for the Artifact Consumer URL in the SAML bridge configuration wizard screen and click on Save, and Finish the installation.

11. Once the installation is complete, a web site named saml-bridge-for-windows is created with two virtual directories, GSA-simulator and saml-bridge.


# Post-Installation Configurations #

Granting access permissions for the SAML bridge log file (i.e. ac.log file) for all users is done using the installer, and is no longer part of the manual step post-installation. However, setting the authentication requirements for the saml bridge Login.aspx page will still be a part of the manual step post-installation and can be found http://code.google.com/apis/searchappliance/documentation/68/wia/wia.html#config_web_security_IIS7

The steps for configuring the SAML bridge can be found on site http://code.google.com/apis/searchappliance/documentation/68/wia/wia.html