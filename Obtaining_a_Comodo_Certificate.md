This article describes the process of obtaining a *User Certificate*.
The certificate will represent the trust in that the user owns the email
address they specified.

Servers identify themselves with a different kind of certificate. If you
are looking for server certificates, this guide is not for you.

## Obtaining a Class 1 certificate from Comodo (Instantssl) using Internet Explorer

Comodo supports IE, Firefox, Opera and Flock, for obtaining the
certificate. All images are click-able if more details are required.

1.  Go to
    <http://www.instantssl.com/ssl-certificate-products/free-email-certificate.html>
2.  Click the Get it free now button next to 'Free Secure Email
    Certificate'
      - ![Instantssl_ie_1.jpg](Instantssl_ie_1.jpg
        "Instantssl_ie_1.jpg")
3.  Fill in your details.
      - ![Instantssl_ie_2.jpg](Instantssl_ie_2.jpg
        "Instantssl_ie_2.jpg")
4.  Press agree & continue.
      - ![Instantssl_ie_3.jpg](Instantssl_ie_3.jpg
        "Instantssl_ie_3.jpg")
5.  Wait for the confirmation mail to arrive in your mailbox.
6.  Follow the instructions in the mail (or go to [this
    link](https://secure.comodo.net/products/!SecureEmailCertificate_Collec2)),
    it should look something like this:
      - ![Instantssl_ie_email.jpg](Instantssl_ie_email.jpg
        "Instantssl_ie_email.jpg")
7.  Enter your email address and the security code given in the mail
      - ![Instantssl_ie_4.jpg](Instantssl_ie_4.jpg
        "Instantssl_ie_4.jpg")
8.  Certificate should be collected and installed in your browser
      - ![Instantssl_ie_5.jpg](Instantssl_ie_5.jpg
        "Instantssl_ie_5.jpg")
9.  Export the certificate to a file
      - Export the certificate (Internet Explorer 8):
        Select from "Tools" -\> "Internet Options" -\> "Content" -\>
        "Certificates" -\> "Personal" and locate your certificate from
        the list. If this is your first certificate it will be listed
        under the name "UTN-USERFirst-Client Authentication and Email".
        Click on "Export" -\> "Next" -\> "Yes, export the private key"
        -\> "Next" -\> "Next". Choose a password for your file and click
        "Next", choose a name for this backup file and save it at a
        known location.
      - Export the certificate (Firefox 3.5)
        Select "Preferences" -\> "Advanced" -\> "Encryption" -\> "View
        Certificates", choose the "Your Certificates" tab and locate
        your certificate from the list. The certificate will be listed
        with "UTN-USERFirst-Client Authentication and Email" as its
        name. Select the certificate and click on "Backup", choose a
        name for this backup file, provide a password and save it at a
        known location.
      - Export the certificate (Opera 10.10)
        Select "Tools" -\> "Preferences" -\> "Advanced" (tab) -\>
        "Security" -\> "Manage Certificate" (button) -\> "Personal"
        (tab) choose your certificate and click "Export" (button).

## I cannot connect after installing my certificate

If you cannot connect and "SSL Error: The root CA certificate is not
trusted for this purpose" is logged to the server log, this is usually
due to having an incomplete certificate bundle.

Please export the certificate using Firefox and try again. Chrome and
Safari are known to create incomplete certificate bundles.

[Category:Documentation
English](Category:Documentation_English "wikilink")