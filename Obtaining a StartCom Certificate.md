# deprecated

{{Notice
|message=StartCom is terminating business on 2018-01-01, and their certificates are already not trusted by major browsers after several incidents. More information is available  [here](https://groups.google.com/forum/#!msg/mozilla.dev.security.policy/LM1SpKHJ-oc/ReT-B5lgAQAJ).}}

The following guide describes how to obtain a free StartCom Class 1 S/MIME certificate using Firefox 3.5. StartCom unfortunately does not support Internet Explorer 8 at this time. As of 2014 Chrome has been tested and works just fine with StartCom. All images are click-able, if more information is needed.

# Go to https://www.startssl.com and click the top right button. 
![Image](mumble_startcom_ff_1_small.jpg)
# Click the sign-up button.
![Image](mumble_startcom_ff_2_small.jpg)
# Fill in your details. Press continue. Now there could be a slight wait while they manually check your details. You really need to provide your actual address and phone number in order for this part of the process to go smooth. StartCom review the applications manually, but rather quickly under normal circumstances. If all goes well you should get a confirmation code to the email address you entered.
![Image](mumble_startcom_ff_3_small.jpg)
# Enter the registration code you get in your mail.
![Image](mumble_startcom_ff_4_enter_code_small.jpg)
# Wait for an activation link to arrive in your mailbox, and click the link in the mail and enter the code that's provided in this new mail. 
#; The mail should look something like this:
![Image](mumble_startcom_ff_email.jpg)
[[
# Now choose to create your certificate. Generate Private Key. The default is High grade, and you should stick with that.
![Image](mumble_startcom_ff_6_generate_key_small.jpg)
# The certificate will be created and stored in the browser. 
![Image](mumble_startcom_ff_7_install_key_small.jpg)
![Image](mumble_startcom_ff_8.jpg)
# To export the certificate select "Preferences" -> "Advanced" -> "Encryption" -> "View Certificates", choose the "Your Certificates" tab and locate your certificate from the list. The certificate will be listed under StartCom Ltd. with "StartCom Free Certificate Member" as its name if this is your first one. Select the certificate and click on "Backup", choose a name for this backup file, provide a password and save it at a known location.
![Image](export_ff_1.jpg)
# :Mumble_Import_Certificate

