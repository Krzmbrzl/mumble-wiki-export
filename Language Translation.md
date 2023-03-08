'''Please refer to the new  [documentation](https://www.mumble.info/contribute/#translation Translation).'''

##Registering to our Forums
This step is optional but we still believe it is a good idea:

If you don't have one already you should register an account  [forums](http://forums.mumble.info/ on our).

If you have any trouble the steps below or any other questions with regards to translating Mumble the  [sub-forum](http://forums.mumble.info/viewforum.php?f=18 Translations) is the ideal place to ask.

##Testing The Results (intended for developers only)
To test the resulting translation click on the entry "mumble_en.ts" and then "Download for use"

In order for the Mumble client to use the translations the ts file will have to be converted to a qm file. Open the ts file you downloaded with Qt Linguist, and then “Release as” to save a qm file, naming it mumble_<lang-shorthand>.qm.

Go to your Mumble folder and place the mumble_*.qm file next to the Mumble executable (e.g. <code>mumble.exe</code> on Windows). Now start Mumble and make sure that your language is set in the user interface section of the Mumble configuration. The language should be displayed in Mumble after you restart the client.

## Fixing errors in the original English strings 
If you find a typo or an error in the original English text please report it to our  [tracker](https://github.com/mumble-voip/mumble/issues issue) and we will fix it. If you feel comfortable around source code and git you can also directly fix the issue in the source and provide us with a pull request on github. Your commit for that should only contain the fix and should not touch the .ts files. If you want you can run  [scripts/updatetranslations.sh](https://github.com/mumble-voip/mumble/blob/master/scripts/updatetranslations.sh) to generate a commit to update the mumble_en.ts file from the Mumble sources but we can do that for you. No other .ts files need to be changed as our transifex workflow will have them automatically updated by our transifex bot as soon as it picks up on the update.




