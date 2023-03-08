This article describes the process of obtaining a ''User Certificate''. The certificate will represent the trust in that the user owns the email address they specified.

Servers identify themselves with a different kind of certificate. If you are looking for server certificates, this guide is not for you.

## Obtaining a Class 1 certificate from Comodo (Instantssl) using Internet Explorer 
{{Notice
|message=Getting the certificate with Chrome/Safari (webkit based) might seem to work at first, but you end up with an incomplete certificate bundle! Consider using an alternative browser.
}}
Comodo supports IE, Firefox, Opera and Flock, for obtaining the certificate. All images are click-able if more details are required.

# Go to http://www.instantssl.com/ssl-certificate-products/free-email-certificate.html 
# Click the Get it free now button next to 'Free Secure Email Certificate' 
![Image](instantssl_ie_1.jpg)
# Fill in your details.
![Image](instantssl_ie_2.jpg)
# Press agree & continue. 
![Image](instantssl_ie_3.jpg)
# Wait for the confirmation mail to arrive in your mailbox.
# Follow the instructions in the mail (or go to  [link](https://secure.comodo.net/products/!SecureEmailCertificate_Collec2 this)), it should look something like this: 
![Image](instantssl_ie_email.jpg)
# Enter your email address and the security code given in the mail 
![Image](instantssl_ie_4.jpg)
# Certificate should be collected and installed in your browser 
![Image](instantssl_ie_5.jpg)
# Export the certificate to a file
#;Export the certificate (Internet Explorer 8):
#:Select from "Tools" -> "Internet Options" -> "Content" -> "Certificates" -> "Personal" and locate your certificate from the list. If this is your first certificate it will be listed under the name "UTN-USERFirst-Client Authentication and Email". Click on "Export" -> "Next" -> "Yes, export the private key" -> "Next" -> "Next". Choose a password for your file and click "Next", choose a name for this backup file and save it at a known location. 
#;Export the certificate (Firefox 3.5)
#:Select "Preferences" -> "Advanced" -> "Encryption" -> "View Certificates", choose the "Your Certificates" tab and locate your certificate from the list. The certificate will be listed with "UTN-USERFirst-Client Authentication and Email" as its name. Select the certificate and click on "Backup", choose a name for this backup file, provide a password and save it at a known location.
#;Export the certificate (Opera 10.10)
#:Select "Tools" -> "Preferences" -> "Advanced" (tab) -> "Security" -> "Manage Certificate" (button) -> "Personal" (tab) choose your certificate and click "Export" (button). 

# :Mumble_Import_Certificate

## I cannot connect after installing my certificate 

If you cannot connect and "SSL Error: The root CA certificate is not trusted for this purpose" is logged to the server log, this is usually due to having an incomplete certificate bundle.

Please export the certificate using Firefox and try again.  Chrome and Safari are known to create incomplete certificate bundles.


