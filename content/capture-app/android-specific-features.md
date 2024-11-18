# Generic features { #capture_app_generic }

## Login { #capture_app_generic_login }

There are two ways to access the application:

1. Manual: The user must type the corresponding URL of the server to be used and enter the username and password.

    > **Note**
    >
    > Take note that login is only possible with servers from version 2.29.

2. QR: The user can use a QR code instead of typing the URL but username and password must be entered manually.

![](resources/images/capture-app-image63.png){ width=25%}

> **Note**
>
> 1. After a succesful login the DHIS2 Android App will keep these values cached (URL and username) and will suggest them for future connections without having to type them.
>

After a succesful login the user should be able to perform an *offline* login only (only avaialble for the last combination of URL/Username). Offline usage gives the possiblity of using the application withou any type of connectivity. All data will still be stored and user can perform a synchornization once the connection is restablished or avaialble.
 

> **Warning**
> 
> In DHIS2 versions up to 2.30 if a user attemps an on-line login and their account has been disabled as explained in the [DHIS 2 Manual - Disable User](https://docs.dhis2.org/master/en/user/html/dhis2_user_manual_en_full.html#disable_user) all the data will be wiped from the phone. Make sure that before disabling a user all the data has been synced or that you are using this feature to remotely wipe sensitive data in case of a device getting lost.
>
> Due to a change in the login API this feature is not available in 2.31, 2.32, 2.33, 2.34, 2.35 and 2.36.

## Offline Multi-user { #capture_app_generic_multiuser}

The Android app have removed the limitation on the number of offline accounts that users can create, allowing them to work with as many offline accounts as needed.

The users will need to have access to the internet for the first login of each account and will be able to switch accounts after without requiring access to the Internet.

![](resources/images/capture-app-image185.png){ width=25%}
![](resources/images/capture-app-image186.png){ width=25%}

The users will be able to manage the user accounts and delete accounts if needed.

![](resources/images/capture-app-image187.png){ width=25%}
![](resources/images/capture-app-image188.png){ width=25%}
![](resources/images/capture-app-image189.png){ width=25%}
![](resources/images/capture-app-image190.png){ width=25%}

## Account Recovery { #capture_app_generic_recovery }

The users will be able to restore their own password if they have the setting enabled: Enabled User Account Recovery.

![](resources/images/capture-app-image64.png){ width=25%}

## Blocking session (PIN) { #capture_app_generic_PIN }

User is able to lock the session using a 4 digit PIN. This allows to move to other apps in your phone without deleting the local data.
If the user forgets the PIN number, log in by entering the credentials is also available.

![](resources/images/capture-app-image65.png){width=25%}

## Biometrics login (Improved 3.1.0) { #capture_app_generic_biometrics_login }

User is able to use the fingerprint scanner or face id if the feature is activated in the device. This will only be available if there is only one account (not supported for multple accounts)

* When the fingerprint scanner is enable and not the PIN, every time the app closes, goes to background or the device is blocked, the session will be locked. Once the app is open again, the user needs to tap the fingerprint icon to activate the scanner.
* If the PIN and the fingerprint are set, when the session is locked and the user open the app again, the PIN will be asked.

![](resources/images/capture-app-image104.jpg){width=25%}
![](resources/images/capture-app-image105.jpg){width=25%}

## Instructions/information buttons { #capture_app_generic_instructions }

A contextual guide is available in TEI dashboard screen.

![](resources/images/capture-app-image66.png){width=25%}

> **Tip**
>
>  User is able to re-open<!-- PALD: unnecessary: (trigger)--> the instructions by clicking on the three dots at the top right corner of the screen.

## Filter { #capture_app_generic_filter }

A filter can be applied in all listing screens (home, event listing, tei search and dataSets) which narrows down the data displayed. The filters available are: period, org. unit, sync state, event status, category option combination and "assigned to me".

![](resources/images/capture-app-image19.png){ width=25%}
![](resources/images/capture-app-image123.png){ width=50%}
![](resources/images/capture-app-image134.png){ width=25%}

Filters will adapt to the different programs and data sets.

1. Program without registration: Date, Org. Unit, Sync State, Event Status and, Category Combination.
2. Program with registration: Event Date, Date of enrollment, Org. Unit, Sync, Enrollment Status, Event Status and Assigned to me. The filter icon will show only if a list of events is available (Display front page list feature or search)
3. Data Sets: Period, Org. Unit, and Sync State.

### Assigned to me { #capture_app_generic_filter_assigned }

It is possible to filter events based on its assignment to the current user. The “Assigned to me” filter has been added to the single event program list, the TEI list and the TEI Dashboard and the map views. It will only be displayed when the active program is configured to assign events to users.

### Event Date/Date/Period { #capture_app_generic_filter_date }

Filter the Events, TEIs(based on their events) and data sets, the following periods of time are availables:
- Today
- This week
- This month
- Yesterday
- Last week
- Last month
- Tomorrow
- Next week
- Next month
- From-to
- Other (Opens a date picker)
- Anytime

### Org. Unit { #capture_app_generic_filter_orgunit }

Allows the user to type the search or select an organisation unit from the tree. The filter will not be visible if the user has only one Organisation Unit configured.

### Sync { #capture_app_generic_filter_sync }

Filer by:
- Synced (events, TEIs, Data Sets)
- Not Synced
- Sync Error
- SMS Synced

### Event Status { #capture_app_generic_filter_event }

Filter the events by:
- Open
- Schedule
- Overdue
- Completed
- Skipped

Multiple status selection is permited. Once you open a TEI, the filter will be kept in the dashboard and show only the events with the selected status.

Events shown are up to 5 years old.

### Date of Enrollment { #capture_app_generic_filter_date_enroll }

The 'Date of Enrollment' will apply to the Enrollment date of the TEI in the program. If there is more than one enrollment date, it should sort the results by the most recent one. The label of this filter will display when available.

### Enrollment Status { #capture_app_generic_filter_enroll_status }

The filter 'Enrollment status' offers three options: Active, Completed, Cancelled. Only one option can be selected at time. If you filter by "completed" and the TEI has more than one enrollment, the app will open the "active"  enrollment. To see the completed one, select the three dot menu at the top right corner of the dashboard and select "program enrollments".

### Follow-Up

The 'Follow Up' filter allowes the user to filter out the TEIs that have been marked as 'Follow-up'. TEIs can be marked to be followed up in the TEI Dashbaord.

### Filtering added in TEI Dashboard: { #capture_app_generic_filter_tei }

Filters have been added to the TEI dashboard. It is possible to filter the events of a Tracked Entity Instance enrollment per period, organisation unit, sync status, event status, and user assignment.

![](resources/images/capture-app-image114.png){ width=25%}

## Sorting { #capture_app_generic_sorting }

Sorting has been integrated in the filter menu.

The sorting button will be on the filter bars with the following behavior:
- Only one sorting applies at a time. If the user clicks a different one, the previous one is disabled.
- The icon for applied sorting shows it is active, the others are inactive.  
- Repeated clicks keep changing the order to the reverse.

![](resources/images/capture-app-image135.png){ width=25%}

### Dates (Period, Date, Event Date or Enrollment Date) { #capture_app_generic_sorting_dates }

- Event Date preceds due date, only use due date when there is no event date.
- Order from most recent to less recent. Future events (due date) goes first.

### Org. Unit { #capture_app_generic_sorting_orgunits }

- List will be sorted in alphabetical order by org unit name.

### Enrollment Status { #capture_app_generic_sorting_enrollment }
- List will be sorted in alphabetical order by status name.

![](resources/images/capture-app-image123.png){ width=100%}

## Sync Information { #capture_app_generic_sync_info }

### Login Sync {#capture_app_generic_login_sync}

During the metadata download, the app will remain in the splash screen and will open the home screen once the metadata is in the device.

In the home screen, the app will inform with a loading spinner on each program when the data is downloading. After the sync process finishes, the app will display one of the two possible icons:

* A green checkmark if the program downloads data successfully and without errors (the icon will disappear after three seconds)  or,
* A gray arrow if there is an error during the sync process and the total or partial data isn't donwloaded
  
The user will be able to see how many programs are downloading data, or completed, making the waiting process more transparent and informative about its progress.

![](resources/images/capture-app-image207.png){ width=20%}

**NOTE:** All programs and data sets will be blocked until the sync process is fully finished.

### Subsequent logins {#capture_app_generic_subsequent_login}

The application will launch a sync process for data and metadata only for the first time the user logs in. In order to facilitate the work in the most difficult cases, the sync process have been removed for the subsequent logins. This means that when the user opens the app, it will open without performing a full sync even if the user logs out of the account.

If the user deletes the account, then the next login will launch the sync process.

Also, users have the option to sync with the server through the Refresh button any time they wish.

### Sync Status {#capture_app_generic_sync_status}

Next to each program or data set an icon will be displayed which allows the user to check sync information. Synced records will not show display any icon. Unsynced (grey arrows), error (red arrows), warning (orange) or SMS (blue and including the SMS word inside) icons are be displayed according to the status.

![](resources/images/capture-app-image67.png){ width=20%}
![](resources/images/capture-app-image69.png){ width=20%}
![](resources/images/capture-app-sync-status.png){ width=20%}

### Granular Sync { #capture_app_generic_sync_granular }

Users can click on the grey arrows (which means record(s) stored online in the device) to perform a sync. These options are available at top level (programs/dataset) or individually (TEI, events, datavalues).

![](resources/images/capture-app-image89.png){ width=25%}
![](resources/images/capture-app-image161.png){ width=25%}


### SMS Sync { #capture_app_generic_sync_sms }

When there is no Internet conection (either via WiFi or Mobile Data) but there is still mobile conectivity, users can synchronize via SMS if the gateway has been previously established in the app and properly configured at server level. 

If the app has been downloaded from Google Play users will have to send manually the SMS from their default SMS app (their default SMS application will open with the message composed). Users should send the message without modifying it and then switch back to the DHIS2 app to confirm that the message was sent.

![](resources/images/capture-app-sms-sync.png){ width=25%}
![](resources/images/capture-app-sms-sync-default-app.png){ width=25%}
![](resources/images/capture-app-sms-sync-confirm.png){ width=25%}

However, if the app has been downloaded from Github (or the training version is being used) the App will just ask for a confirmation to send one or several messages (SMS) and will send them in the background (without opening the default SMS application).

![](resources/images/capture-app-sms-sync-training.png){ width=25%}
![](resources/images/capture-app-sms-sync-confirm-training.png){ width=25%}
![](resources/images/capture-app-sms-synced-training.png){ width=25%}

> **Tip**
>
>  Edit parameters related to SMS gateway in the SMS Settings (Settings Menu) or set this globally via the [#capture_app_android_settings_webapp_general](Android Settings Web App)

![](resources/images/capture-app-image90.png){ width=25%}

> **Note**
>
>  Note that in order to user the SMS sync capabilities the SMS services needs to be enabled in the server side as described in the [https://docs.dhis2.org/master/en/dhis2_user_manual_en/mobile.html#sms-service](oficial documentation). You can also find more information on how to use different gateways in the [https://docs.dhis2.org/master/en/dhis2_android_implementation_guideline/about-this-guide.html](Android Implementation Guidelines)

### Meta data sync error { #capture_app_visual_sync_error }

In case of errors during the sync process, a message is displayed in the settings menu ('Sync data' or 'Sync configuration' section). Also, a red sync icon is displayed next to the program in the Home screen. The sync error log gives details about the error and is prepared to be shared with admins.

![](resources/images/capture-app-image43.jpg){ width=25%}
![](resources/images/capture-app-image11.png){ width=25%}

You can also open the sync errors log from **Settings**:

![](resources/images/capture-app-image15.jpg){ width=25%}

## Refresh data { #capture_app_generic_refresh_data }

Users can now retrieve the latest data from the server before entering new data. A refresh button is now located to trigger a granular synchronization in the following screens:

* Home
* Search
* TEI dashboard
* Event program listing
* Event details
* Data set listing
* Data set details

![](resources/images/capture-app-image19.png){ width=25%}
![](resources/images/capture-app-image191.png){ width=25%}
![](resources/images/capture-app-image192.png){ width=25%}
![](resources/images/capture-app-image193.png){ width=25%}

## Org unit { #capture_app_generic_orgunit }

![](resources/images/capture-app-image30.png){ width=25%}

The whole organisation unit tree is displayed. Organisation units not available for data entry will be colored in grey.
User must check the box to select the org unit wanted. After an organisation unit is selected, the parents will be marked in bold to show hint of the organisation unit selection when opening the hierarchy.

![](resources/images/capture-app-image194.png){ width=25%}

> **Caution**
>
>  Mobile users are not expected to access the org. unit hierarchy of a whole country. Maximum number of org units is difficult to set, as the App does not set the limit, but the resources on the device (memory, processor). We could say below 250 org units should be safe, but still believe that is a very big number for a mobile use case.


## Data Sets { #capture_app_generic_datasets }

The user can now enter aggregate data for an organisation Unit, a period and a set of data elements and send it to the server.

![](resources/images/capture-app-image87.png){ width=25%}
![](resources/images/capture-app-image93.png){ width=25%}
![](resources/images/capture-app-image92.png){ width=25%}


## Home (Improved 3.1.0) {#capture_app_home}

The home screen of the DHIS2 Android App shows the list of programs and data sets available for the user. The first thing the user does when collecting data in this case is to select the program or data set to work with.

In 3.1.0,  a new dynamic home screen that adapts to the number of programs (up to 4 programs) available has been implemented. This update replaces the old static list that didn’t adjust to the screen, providing a more responsive and user-friendly interface.The responsive design makes better use of screen real estate, providing a more engaging and functional home screen layout.


![](resources/images/capture-app-image310.png){ width=25%}
![](resources/images/capture-app-image313.png){ width=25%}


> **Tip**
>
>  An easy way to differentiate them is by looking at the word at the bottom left corner. The word 'Event' will always be in event programs. In tracker will appear the name of the tracked entity type (person, patient, building, etc.). For data sets, the word 'DataSets' will be shown next to the number of records.

For those implementations where the users have access to only one program or dataset, the App will skip the home and will open directly the program or datasaset screen with the event, TEI or dataset list to reduce the number of clicks and streamline the process of data entry.

![](resources/images/capture-app-image245.png){ width=25%}
![](resources/images/capture-app-image247.png){ width=25%}

## Sharing Data { #capture_app_generic_shargin }

Users can share TEI via QR codes. This allows transferring/sharing information between devices without the need of transferring via the server (useful when connecitivity might be missing). To do this users should open any TEI and click on the *SHARE* button.

![](resources/images/capture-app-image72.png){ width=25%}
![](resources/images/capture-app-image73.png){ width=25%}


## Capture Coordinates { #capture_app_generic_capture_coord }

### TEI coordinates { #capture_app_generic_capture_coord_tei }

Capture the TEI coordinates in the registration form.  Enable this feature in the TET feature type.

![](resources/images/capture-app-image94.png){ width=25%}

### Polygons { #capture_app_generic_capture_coord_polygons }

The app now supports the geoJSON format and the user is able to capture polygons.

![](resources/images/capture-app-image95.png){ width=25%}


## Images { #capture_app_generic_images }

ValueType image can be used in Android to capture data and also, depending on the program configuration to be displayed in the TEI dashboard. When this value type the first data element/attribute marked as displayed in the program configuration it will be used as the TEI profile image.

![](resources/images/capture-app-image99.png){ width=25%}
![](resources/images/capture-app-image98.png){ width=25%}
![](resources/images/capture-app-image100.png){ width=25%}

Open the TEI profile image by clicking on it.

![](resources/images/capture-app-image138.png){ width=25%}


## Display events and TEIs in maps { #capture_app_generic_display_events }

When a program stage or tracked entity type have a feature type (and for programs with registration the option displayFrontPageList is enabled) the listings can be switched to display the information in a map. Make the switch by clicking on the map icon in the navigation panel.


![](resources/images/capture-app-image101.png){ width=25%}
![](resources/images/capture-app-image102.png){ width=25%}

If the TEI has a profile image, the map will display it.

![](resources/images/capture-app-image103.png){ width=25%}

## Personalized Calendar View { #capture_app_personalized_calendar }

In the DHIS2 Android Capture App users can switch date selection from spinner to calendar view. In this version, the app will remember the last visualization selected by the user and use it the next time the user needs to select a date.

![](resources/images/capture-app-image177.png){ width=25%}

## Reason for non-editable data { #capture_app_reason_non_editable }

Data can be blocked for many reasons in DHIS2, because of access restrictions or expiration among others. When an Event, TEI or Data Set are not editable the user will be able to find the reason on the "Details" section.

The following list contains all possible reasons:

* Event completion
* Enrollment completion
* Expired event
* Closed organization unit
* Organization unit out of capture scope
* No access to capture data in the program or data set
* No access to a category option in the program or data set

![](resources/images/capture-app-image178.png){ width=25%}
![](resources/images/capture-app-image179.png){ width=25%}

## Configuration troubleshooting { #capture_app_configuration_troubleshooting }

This feature is for administrators. The Android App incorporates an option in the settings screen for verifying some aspects of the DHIS2 configuration.

![](resources/images/capture-app-image188.png){ width=25%}
![](resources/images/capture-app-image195.png){ width=25%}

* **Language:** the user will be able to change the language of the application user interface to identify labels, buttons or prompts with errors or without translation.

![](resources/images/capture-app-image196.png){ width=25%}
![](resources/images/capture-app-image197.png){ width=25%}

* **Program rule validation:** this validator will check the program rules in the device and display configuration inconsistencies.

![](resources/images/capture-app-image198.png){ width=25%}
![](resources/images/capture-app-image199.png){ width=25%}

## Error Navigation { #capture_app_error_navigation }

The Android App has improved the navigation of sync errors on the user interface. The app will display the sync errors in a simple and clean manner allowing the user to navigate from the home screen to the exact field that is causing the error inside the event or data set.

![](resources/images/capture-app-image217.png){ width=25%}

User must tap on any of the errors listed and the app will move to the correspondent screen. Once the error is located and fixed, the user can synced by tapping on the "Refresh" button.

![](resources/images/capture-app-image218.png){ width=25%}
![](resources/images/capture-app-image219.png){ width=25%}
![](resources/images/capture-app-image220.png){ width=25%}

## LMIS Module { #capture_app_lmis_module }

The new module for real stock monitoring use case enables users to manage and monitor their stock levels in real-time. Integrating a module implies that the app will open a completely new and different user interface and experience to respond to a different data entry flow. To use this modules the program will need to be configured using the new web app for program use case configuration.

![](resources/images/capture-app-image221.png){ width=25%}
![](resources/images/capture-app-image222.png){ width=25%}
![](resources/images/capture-app-image223.png){ width=25%}
