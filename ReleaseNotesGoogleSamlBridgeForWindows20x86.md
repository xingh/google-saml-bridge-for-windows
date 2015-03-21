# Release Notes for Google SAML Bridge for Windows 2.0 32-bit #

Release Notes


Google SAML bridge for Windows 2.0 (32-bit)

This document contains the release notes for Google SAML bridge for Windows 2.0 (32-bit).
The following sections describe the release in detail and provide information that supplements the main documentation.
See the Issues Tab on the Code Site for the current list of known issues and workarounds.

Web Site: http://code.google.com/p/google-saml-bridge-for-windows/issues/list


Release 2.0, 31 March, 2011


INTRODUCTION

---

This is an early access release for wide evaluation and usage. Your feedback is important to us. Keep in mind that we are continuing to work on Google SAML bridge for Windows 2.0 (32-bit) and things may change in the future.

Pre-requisites

---

**Windows Server 2003 Enterprise server/Windows Server 2008 Enterprise server.** Microsoft .Net Framework 2.0.
**IIS 6.0/IIS 7.0.**

Note:

---

If you have already installed Google SAML bridge for Windows earlier using the old installer (i.e. Google SAML bridge for Windows.msi), please uninstall it before trying the Google SAML bridge for Windows 2.0 installer.

Features

---

Google SAML Bridge for Windows allows users to gain seamless access to content that resides on file systems, web servers, or Microsoft Office Sharepoint servers.

Platform Support

---

Google SAML bridge for Windows 2.0 (32-bit) can be installed on Windows Server 2003 Enterprise (32-bit)/Windows Server 2008 Enterprise (32-bit) Operating System.

Note:

---

> a) There are separate installers for 32-bit and 64-bit Operating System.
> b) The 64-bit installer is supported on machines with x64 platform.


Certified Against

---

Microsoft Windows Server 2008
Enterprise Edition
Intel  Xeon  CPU
E5504 @ 2.00GHz, 4.00 GB of RAM

Microsoft Windows Server 2003
Enterprise Edition
Intel  Xeon  CPU
E5504 @ 2.00GHz, 2.00 GB of RAM

Known Issues/Limitations

---

1. The Installer does not validate the port number for 'Google SAML bridge for Windows'. User needs to enter a valid non-conflicting port during installation. Assigned port number could be changed even after Installation directly through IIS Manager.
2. The Installer does not validate the 'Artifact Consumer' URL on "Google SAML Bridge for Windows - Configuration Wizard".
3. Cancelling Installer does not initiate rollback of the installed components. You need to run installer again in 'remove' mode to clean up the installed components.
4. Google Search Resource Kit for SharePoint and Google SAML bridge for Windows, if concurrently installed on the same machine, might encounter with error messages.
5. After uninstallation, aspnet\_client folder will still exist in saml-bridge-for-windows folder for MOSS 2007 installation on 32-bit machine with IIS 6.0
6. Need to select Remove or Repair manually during the Uninstallation.
7. Sometimes an error message(unable to parse incoming SOAP message: SAML exception: Could not validate input xml against schema:..) will be encountered in the Authorization logs, if Google Search Box for SharePoint is not deployed on all WFE.
8. If the 32 bit installer is executed on 64 bit machine, then the installer does not give any error message.