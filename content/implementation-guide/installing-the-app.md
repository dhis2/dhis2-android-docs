# Installing the new DHIS 2 Capture App { #implementation_guide_installing }


There application can be downloaded and installed from two places:

- [**Google Play:**](https://play.google.com/store/apps/details?id=com.dhis2&hl=en_US) - This version has certain security measures implemented and does not allow screen broadcasting or taking screenshots by default unless configured specifically using the Android Settings Web App. For SMS syncing, users must manually send the autocomposed message from their default messaging app and confirm afterwards.
- [**GitHub**](https://github.com/dhis2/dhis2-android-capture-app/releases) - There are two versions available in Github:
	- Production version: Almost exactly as the version in Google Play, it does not allow screen broadcasting or taking screenshots by default unless configured specifically using the Android Settings Web App. However, the SMS syncing workflow does not require manually sending the SMS via the default messaging app.
	- Training version: With screen broadcasting, possibility to take screenshots, debugging libraries, etc (the one named with the suffix \_training.apk)

> **Note**
>
> When installing the training APK, you might need to allow 3rd party installs.
> 
> Before 2.7 the production version came in two versions: one included SMS capabilities and the other did not.

Please read the section on App distribution for understanding the implications of using the different distribution channels.

## Migrating from the old apps { #implementation_guide_installing_migrating }


Before you start with the installation of the new DHIS 2 Capture Android App in the field, it is important to note that if your users are already using the old generation DHIS 2 Android Event Capture or Tracker Capture, they should follow these steps:

1. Sync data of the current DHIS 2 app you are using
2. Download and install the new DHIS 2 Android Capture App
3. Login using your credentials.

> **Warning**
>
> Deleting the app without syncing can cause information loss.
>

## Login into the app { #implementation_guide_installing_login }


In order to log in you will need the DHIS 2 server URL, the user name and the password for the user you just created. For testing purposes you can also use the testing servers and credentials:

| URL | User | Password |
| ------------- | --- | --- |
| Most recent DHIS 2 version <br /> [https://play.dhis2.org/demo](https://play.dhis2.org/android-current) | android | Android123 |
