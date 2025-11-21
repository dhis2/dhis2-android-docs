# Android Settings Web App { #capture_app_android_settings_webapp }
## Overview { #capture_app_android_settings_webapp_overview }

This section focuses on the [Android Settings Web App](https://apps.dhis2.org/app/a1bd6b5b-de8c-4998-8d34-56c18a139683) implementation.


The [Android Settings Web App](https://apps.dhis2.org/app/a1bd6b5b-de8c-4998-8d34-56c18a139683) allows admins to configure synchronization parameters for the DHIS2 Android App, encrypt the local database of the Android devices, customize the appearance of Programs, Data sets, and Home screen, and add TEI Analytics items. The configuration parameters defined within this web app will overwrite the settings of all Android devices using the DHIS2 Android Capture App.

Please note that in this version of the Web App (2.3), if the DHIS2 version is equal to or higher than 2.40, only users with "M_androidsettingsapp" or "ALL" authority can define those parameters in the configuration. Other users accessing the web app can see the value of the parameters but cannot edit them.

> **Warning**
>
> If the DHIS2 version is not above 2.40, only users with 'ALL' authority can define those parameters in the configuration.
> 


## General settings { #capture_app_android_settings_webapp_general }

Includes configurations such as the Matomo URL and project ID, the number of reserved values to download per TEI, and encrypt the device database.

![](resources/images/capture-app-general-settings.png)

### Matomo configuration { #capture_app_android_settings_webapp_general_matomo }

The DHIS2 Android App sends anonymize analytics that can be used to evaluate performance and/or detect problems at an early stage. [Matomo](https://matomo.org) is the tool used for this and running in a specific server not accessible to the general public. However, implementations can set up their own
 Matomo instance (or using the cloud version) in order to collect and analyse the statistics. 

Once you have your Matomo instance ready you should get the URLs and the project ID like shown in the picture below (left). The ID can be introduced directly but the URL needs to be followed with */matomo.php* and start with *https* or *http* as shown below (right).

![](resources/images/capture-app-matomo-instance.png){width=33%}
![](resources/images/capture-app-matomo-settings.png){width=33%}


### Mobile configuration { #capture_app_android_settings_webapp_generalmobile_configuration }
This section allows admin users to edit the SMS gateway ad result sender phone number.
This configuration can be found in the Android app.
- Click on Settings
- Click on SMS Settings

![](resources/images/capture-app-sms-settings.png){width=33%}

### Reserved values { #capture_app_android_settings_webapp_general_reserved_values }
This will specify the number of values per TEI attribute reserved to download in the devices. By default, the Android App reserves 100 Ids, but it is possible to add or reduce this number.

To find this configuration in the Android app:
- Click on Settings
- Click on Reserved Values
- To refill them click on *Manage Reserved Values*

![](resources/images/capture-app-reserved-values.png){width=33%}
![](resources/images/capture-app-reserved-values-refill.png){width=33%}

### Encrypt device database { #capture_app_android_settings_webapp_general_encrypt_database }
This will force all the devices to store the database encrypted increasing the security level against data theft attacks.

By default, the DHIS2 Android App database is not encrypted, but an admin can check the *Encrypt device database* to encrypt the metadata and data stored in every device. Encrypting the database will have an impact on the database volume and performance (degradation between 10-15%) of the Android app. Note that at the moment of selecting or unselecting this option, no data is lost (even if it hasn't been previously synchronized with the server)

> **Warning**
>
> This is a critical action and will affect the local database of all Android devices synchronizing with the server (it won't affect the server DHIS2 database).
>
> By default, the Android app database is not encrypted, but an admin can check the *Encrypt device database* to encrypt the metadata and data stored in every device. Encrypting the database will have an impact on the database volume and performance of the Android app. Note that at the moment of selecting or unselecting this option, no data is lost (even if it hasn't been previously synchronized with the server)

### Allow screenshots { #capture_app_android_settings_webapp_general_screenshots }
This section allows to configure the possibility to take screenshots or screen sharing using the Android Capture App (which is required to remote support with applications like Teamviewer, Teams, etc.). Please note that the default behavior is deactivated screenshots.

> **Warning**
>
> The DHIS2 Android App disables the possibility of taking screenshots (and capturing the screen from other apps) by default following security and privacy recommendations. Allowing screenshots might be useful for support and/or sharing purposes in same cases but make sure you understand the security and privacy implications of this setting before enabling it.
>


### Skip DHIS2 version validation (**v2.4**) { #capture_app_android_settings_webapp_general_skip_version_validation }
When connecting to DHIS2 instances, the app typically verifies compatibility with supported versions. However, in some cases, connecting to unsupported instances may be necessary or useful. Please note that the default behavior is to enforce strict version validation. To skip the validation process for DHIS2 version compatibility, select the checkbox.

![](resources/images/capture-app-skip-version-validation.png)

> **Warning**
>
> This option is only applicable when using Android Capture app version 3.0 or later.
>


### Opt-in Features (**v2.3.1**) { #capture_app_android_settings_webapp_general_optin_features }
Opt-in features are additional functionalities or settings within the application that the user can choose to enable based on preferences. Unlike default settings, these features require an explicit consent or action ('opting in') to activate.
Opting in allows the user to customize the experience by adding extra capabilities to the app. Keep in mind that these features might come with specific considerations, so it is recommended to review any associated information before opting in.

To enable a feature:

- Click on *Opt-in Features*. 
- A list of available opt-in settings will appear.
- Click on the feature's checkbox to enable it.

**Data entry Form (**v2.4**):** The inputs for all value types have been redesigned in the Android Capture App with an improved selection mode and increased tappable areas and texts to offer a cleaner and more intuitive user experience. By default, the Android Capture App will display the new forms. Admin users can opt out of using the new version of forms by clicking the checkbox option.

![](resources/images/capture-app-optin-features.png)

### Disable all settings { #capture_app_android_settings_webapp_general_disable_settings }
By clicking this button, the user will remove all Android configuration settings. No configuration will be applied to the Android App (if this is the case, the sync parameters applied are the ones defined in the Android Capture app).


## Synchronization { #capture_app_android_settings_webapp_synchronization }

It offers additional parameters to control metadata/data synchronization.


### Global { #capture_app_android_settings_webapp_synchronization_global }

Metadata sync
:	Admin users can choose how often the metadata will sync. e.g. Sync metadata every 24 hours.

Data sync
:	Admin users can choose how often the data will sync. e.g. Syncing data every 6 hours.

![](resources/images/capture-app-sync-global.png){width=50%}
![](resources/images/capture-app-sync-global-app.png){width=33%}


Use the new Tracker Importer
:	Admin users can choose which tracker importer endpoint will be used.

> **Warning**
>
> This option is only available if the Android Settings Webapp is used from version 2.38 DHIS2 API onwards.
>
> By default, if the DHIS2 API version is 2.38 or higher, the Android app will use the importer introduced in 2.37 */api/tracker* endpoint but an admin can deselect this option and the legacy tracker importer */api/trackedEntityInstances* will be used.
> 
> ![](resources/images/capture-app-sync-global-importer.png){width=50%}
>

Use the new Tracker Exporter (**v2.3**)
:	Admin users can choose which tracker exporter endpoint will be used.

> **Warning**
>
> This option is only available if the Android Settings Webapp is used from version 2.40 DHIS2 API onwards. 
> 
> By default, if the DHIS2 API version is 2.40 or higher, the Android app will use the exporter introduced in the 2.37 */api/tracker* endpoint, but an admin can deselect this option, and the legacy tracker importer */api/trackedEntityInstances* will be used.
>
>
> ![](resources/images/capture-app-sync-global-exporter.png){width=50%}
>

Limit the file size to download (**v2.3**)
:	Admin users can limit the maximum size of the file resources downloaded in KB.

![](resources/images/capture-app-sync-download-file-size.png){width=33%}

> **Note**
>
> Admin users have the ability to set the maximum file resource size for downloads. Admins can now leave the field with no value to indicate no limit on the maximum file size. (**v2.4.1**) 
> - no value: Allows unlimited file resource size for downloads. By default, this is the initial value.
> - 0: Restricts downloads to 0 KB.
> - Any positive value: Restricts downloads to files within the specified maximum size limit (in megabytes or another unit). 
> 
> This provides flexibility for admins to either enforce a file size limit or allow unrestricted downloads depending on their needs.
>



### Program { #capture_app_android_settings_webapp_synchronization_program }

This section controls the program data synchronization parameters. It has a section to define global or default parameters to be used in the synchronization of all programs.

#### Global settings { #capture_app_android_settings_webapp_synchronization_program_global }

Global settings apply to all programs that an Android user has access to. The settings can be enabled globally, per Org Unit, per program or per OU and program.

![](resources/images/capture-app-program-global-settings.png){width=50%}

* TEI to download:	Maximum number of TEIs to download from the server.

* TEI download period:	It downloads the TEIs that have been updated within a period. e.g. TEIs that have been updated within last month

* Event to download:	Maximum number of Events to download (from events programs, see note below).

* Event download period:	It downloads Events which event date belongs to a specific period.

---
**Note**

Administrators may notice that the total number of downloaded events appears higher than expected when configuring limits for both TEIs and Events. This is due to how the Android app applies these limits:

* The TEI limit controls how many tracked entities are downloaded, including all their associated events.
* The Event limit applies only to event programs (programs without registration).
* It does not restrict events belonging to tracker programs.

*Example:*

A tracker program contains TEIs with an average of 5 events each. If the TEI download limit is set to 100, the app will download those 100 TEIs and all their related events (100 × 5 = 500 events).
Additionally, an event program contains 1,000 standalone events, and the Event download limit is set to 200.
In total, the Android app will download:

* 500 events from the tracker program (due to 100 TEIs × 5 events each)
* 200 events from the event program

Resulting in 700 events downloaded overall.

---

#### Specific settings (Improved 3.3.0) { #capture_app_android_settings_webapp_synchronization_program_specific }

Program specific settings allow administrators to override the global synchronization rules for selected programs. This is useful when different programs require different limits or filtering criteria.

To configure program-specific settings:

1. Click Add a Program-specific setting.

2. Select a program under Values per Program.

3. Configure the available parameters (varies depending on program type).

**Available Parameters**

Program specific settings differ depending on whether the program has registration (Tracker) or does not have registration (Event programs). Each setting appears only when applicable.

1. Programs Without Registration (Event programs)

Parameters may include:

* Setting level – Defines whether synchronization applies to all Org Units or specific Org Units.
* Download events based on predefined list views (NEW in 3.3.0)
* Maximum event downloads
* Download events with event date within (configurable time range)

2. Programs With Registration (Tracker programs)

Parameters may include:

* Setting level
* Maximum TEI downloads per program
* Download TEIs updated within
* Download TEIs based on predefined list views (NEW in 3.3.0)
* Download TEI with status
* Download TEIs with enrollment date within

**Download based on List views (NEW in 3.3.0)**

When a program is linked to one or more working lists, the corresponding filtering fields will behave as follows:

* The Android app syncs TEIs based on the working list(s) assigned to the user.
* If a user has access to one working list → that list is used.
* If the user has access to multiple lists → their content is merged automatically.

![](resources/images/capture-app-image363.png){width=50%}
![](resources/images/capture-app-image364.png){width=50%}

##### Viewing and managing program-specific settings

When one or more program-specific configurations have been saved, they will appear in a summary table.
From this table, administrators can:

* View the current configuration per program
*Edit the values
* Delete the program-specific settings

![](resources/images/capture-app-program-specific-table.png){width=50%}

##### Important Considerations

> **Caution**
Program-specific settings can lead to a larger number of TEIs being downloaded than expected based on the global synchronization limit.
This happens because the Android client performs synchronization in two steps:
>
>1. Global sync: Downloads up to X TEIs based on the user’s organisation units and the lastUpdated field.
>2. Program-specific sync:
Downloads up to Y additional TEIs for each program that has specific settings configured.
>
>If the TEIs included in the global sync were updated more recently than those in a specific program, both sets will be downloaded.
>
>
>*For example:*
>* Global TEI limit = 500
>* Program-specific TEI limit for Malaria Case Diagnosis = 500
>* Global set contains more recent TEIs than the program-specific set
>
>The device may download up to 1000 TEIs in total — 500 from the global step and 500 from the program-specific step.
Although this may seem unexpected at first, it can be used strategically to guarantee minimum TEI numbers for critical programs.

***Example***

Imagine a program called Community Care with 17 TEIs, all updated a long time ago.
The same user also has access to other organisation units with many recently updated TEIs from other programs.

To ensure that all 17 TEIs from Community Care are always downloaded:

Set a low number (e.g., 20) in Global Settings.

Set 17 as the program-specific limit for Community Care.

Initial sync will download:

20 recently updated TEIs (not from Community Care)

17 TEIs from Community Care

Total downloaded = 37 TEIs

#### Reset all values { #capture_app_android_settings_webapp_synchronization_program_reset_all }

By clicking on *Reset all values*, the admin user will restore the default settings values of the program section. Please note that in this case it means no specific settings per program. 

To save any configuration, the admin user needs to click on the *Save* button (this button is disabled for the users who don't have "ALL" or "M_androidsettingsapp" authority)


### Data set { #capture_app_android_settings_webapp_synchronization_data }

This section controls the aggregated data synchronization parameters.

#### Global settings { #capture_app_android_settings_webapp_synchronization_data_global }

The first part is for global settings that apply to all data sets an Android user has access to. 

![](resources/images/capture-app-dataset-global-settings.png){width=50%}

The maximum number of periods defines the amount of past periods the app will download in the data synchronization process.

If a data set has future periods ("open future periods" configuration) the app won't take them into consideration in the restriction of the amounts of periods to download.

For example, in a data set with "open future periods" = 2 and a "maximum number of periods to download" = 1, the app will download 3 periods.

#### Specific Settings { #capture_app_android_settings_webapp_synchronization_data_specific }

To add a specific setting:

- Click on *Add a Data set specific setting*, a dialog with a list of data sets will appear. 
- Click on a data set, and this field will be autocompleted with the default value based on the dataset period type.

![](resources/images/capture-app-dataset-specific-dialog.png){width=50%}

![](resources/images/capture-app-dataset-specific-table.png){width=50%}


### User Sync Test { #capture_app_android_settings_webapp_synchronization_user_sync_test }

This section checks the amount of data and metadata a user would sync to his/her device. You can run this test on any user that you have access to. This test shows up the number of organisation units, data sets, program rules, programs, etc., that an android user has access to (so the resources that the android app will download), and the metadata and data download size (approx estimation). Please note that a user doesn't need to have the "ALL" or "M_androidsettingsapp" authority to run this test.

![](resources/images/capture-app-user-sync-test.png){width=50%}

> **Note:** 
>
> The values that are highlighted in red are because the value is considered greater than the maximum recommended value.


## Appearance { #capture_app_android_settings_webapp_appearance }

These settings give control over the appearance of the data entry and list forms.

- Filter: it defines the filters that can be enabled in the different app menus.
- Completion spinner: it turns on/off the completion spinner that shows the progress in the data entry form.

These settings refer to visual components, so they must be consumed by the app.
For more information about filters feel free to review filters [documentation](https://docs.dhis2.org/en/use/android-app/android-specific-features.html#capture_app_generic_filter). 

### Home screen { #capture_app_android_settings_webapp_appearance_home_screen }

It allows the admin user to enable or disable the option to show the filters related to Date, Organisation Unit, Sync Status, and Assigned to me on the Home screen.

![](resources/images/capture-app-appearance-home.png){width=75%}


### Program { #capture_app_android_settings_webapp_appearance_program }

Program appearance allows to hide/show features within the program according to the configuration needs. These changes can happen globally, applying to ALL the programs, or specifically to a single one.

#### Global settings { #capture_app_android_settings_webapp_appearance_program_global }

Global settings apply to all programs that an android user has access to.

![](resources/images/capture-app-appearance-program-global.png){width=75%}

Percentage (%) complete in Program: 
Enable or disable the option to show the completion percentage of the data entry form.

TEI referrals (**v2.3.1**):	
It allows to switch off/on the TEI referral option.

Collapse sections in form (**v2.3.1**):  
Current behavior lets the sections collapse and expand in an accordion style. This option overrides the behavior by keeping all the sections of the form (registration and events) open and removing the "next" button in each section.	


#### Specific settings { #capture_app_android_settings_webapp_appearance_program_specific }

This section allows the admin user to customize features such as filter, completion percentage, mandatory search, referrals, TEI headers, referral options and collapse sections in form. Each explained in the section below.

To add a specific setting:

- Click on *Add a Program Settings*, and a dialog will appear.
- Click on the dropdown that will show a list of programs.
- Clicking on a program will show the different filters to configure. The category combo filter depends on the category combo name.

![](resources/images/capture-app-appearance-program-specific.png){width=75%}

![](resources/images/capture-app-appearance-program-specific-advanced.png){width=75%}

TEI without searching:
Offer online and offline search, as well as allow the user to create a TEI without a prior search.

TEI Header (**v2.3.1**):
Assign a specific attribute or expression that will be displayed as a header in TEI cards. 

To add a TEI Header:

- Select a Program Indicator
- An expression related to the program indicator will be displayed

![](resources/images/capture-app-appearance-program-specific-tei-header.png)


> **Note:**
>
> A notice box will be displayed if the selected program lacks expressions related to program indicators that are valid for Android. 
> 
> An expression is considered valid for Android only if it is composed exclusively of attributes and/or functions.
> 
> ![](resources/images/capture-app-appearance-program-specific-expression-valid.png)
> 
> ![](resources/images/capture-app-appearance-program-specific-expression-invalid.png)
> 


If any specific settings have been saved, a table will summarize the particular configuration per program, and the options to edit or delete these settings. 

![](resources/images/capture-app-appearance-program-table.png)

The option "Show percentage (%) complete in Program toolbar" refers to: 
![](resources/images/capture-app-appearance-programs-spinner.png){width=50%}

**Search Tracked Entity (v2.2)**

Searching before entering a new TEI is mandatory to avoid possible duplicates, and the DHIS2 Android App has been designed as such. This new version gives the possibility to choose to keep this process or allow the user to create a TEI without searching first.
By default, allowing the user to create a TEI without searching is disabled.

**Capture Coordinates (v2.4.1)**

This section provides admin users with two configurable options for managing location capture on mobile devices:

- Disable Manual Location Capture:
By enabling this option, manual location entry on mobile devices is disabled. This ensures that location data is captured automatically, preventing manual errors or alterations.

- Minimum Location Accuracy:
This field allows admins to define the minimum precision level (in meters) required for capturing location data. The lower the value, the higher the accuracy required. The minimum recommended value is 5 meters, ensuring reliable and precise location capture.

These options provide admins with greater control over how location data is captured and ensure consistency in the accuracy of recorded positions.

![](resources/images/capture-app-appearance-programs-coordinates.png)

**Quick Actions (New 2.4.2)**

The Quick Actions Bar is a new feature in the Android App that allows users to configure and add "chips" representing different actions for easy access in the TEI Dashboard.
This section aims to enhance user productivity by providing a streamlined and customizable interface for frequently used functions.

![](resources/images/capture-app-appearance-programs-quick-actions.png)

> **Note:**
>
> Checking the box will display the action as a "quick-access" chip instead of just listing it in the menu. 
> 
> Chips can’t be reordered. The order of appearance will be:
> - Mark for follow-up
> - Transfer TEI
> - Complete Enrollment
> - Cancel Enrollment
> - More enrollments
>
> By default, all the chips are unselected and the Quick actions bar is not available in the Android app.
>
> ![](resources/images/capture-app-appearance-program-specific-quick-action.png)
>


### Data set { #capture_app_android_settings_webapp_appearance_data }

It allows admins to enable/disable filters for the Data set section

#### Global settings { #capture_app_android_settings_webapp_appearance_data_global }

The first part is for global settings that apply to all data sets an android user has access to.

![](resources/images/capture-app-appearance-dataset-global.png){width=75%}

#### Specific settings { #capture_app_android_settings_webapp_appearance_data_specific }

To add a specific setting:

- Click on *Add a Data set Settings*. A dialog box will pop up with a dropdown with a list of data sets.
- Click on a data set, and a list of options to enable or disable filters will be displayed.

![](resources/images/capture-app-appearance-dataset-specific.png){width=75%}

![](resources/images/capture-app-appearance-dataset-table.png){width=75%}

**Capture Coordinates (New 2.4.2)**

This section provides admin users with two configurable options for managing location capture on mobile devices:

- Disable Manual Location Capture:
  By enabling this option, manual location entry on mobile devices is disabled. This ensures that location data is captured automatically, preventing manual errors or alterations.

- Minimum Location Accuracy:
  This field allows admins to define the minimum precision level (in meters) required for capturing location data. The lower the value, the higher the accuracy required. The minimum recommended value is 5 meters, ensuring reliable and precise location capture.

These options provide admins with greater control over how location data is captured and ensure consistency in the accuracy of recorded positions.

![](resources/images/capture-app-appearance-dataset-coordinates.png)



## Analytics { #capture_app_android_settings_webapp_analytics }

Analytics settings define TEI, Home, Program and Data Set analytics items (charts, tables) that will be displayed to the user. Any item defined in the settings app will overwrite the default behaviour of the android app, only showing the items defined in the settings app. 

Also, even though these analytics are created using the android settings web app, the data aggregation happens offline using only data stored in the device.

### TEI { #capture_app_android_settings_webapp_analytics_tei }

The scope of the analysis is the TEI, so the visualizations will be displayed in the TEI dashboard of the android app.

The purpose of this section is to define visualizations to show evolution of *data elements* and *program indicators* over time. Based on that, it will only take into consideration data elements that belongs to a repeatable program stage, or program indicators which formula contains at least one data element that belongs to a repeatable program stage.

To create a **TEI Analytics** item:

1. Click on *Add TEI Analytics*. A dialog box will pop up with a small form.
2. Choose a program and a repeatable program stage, and fill the form. The **Short name** is the only optional field.
3. If an item visualization other than WHO Nutrition has been chosen, the next fields to select are the period type (monthly, weekly, daily), an element type (Program Indicator, Data Element), and an element that will be based on the element type previously selected. Remember that these elements are related to the program and repeatable program stage chosen at the beginning.

![](resources/images/capture-app-analytics-item.png)

To create a **WHO Nutrition Analytics** item:

1. Select a program, a program stage, and WHO nutrition as visualization type.
2. Choose a WHO visualization type that can be Height for Age (HFA), Weight for Age (WFA) or Weight for Height (WFH).
3. Select the tracked entity attribute that represents the gender. You have then to specify the option for Male 'Male title' and the option for Female 'Female title'. Normally they will be option codes.
4. Choose the data element/program indicator that will be displayed in the Horizontal (x) axis
5. Choose the data element/program indicator that will be displayed in the Vertical (y) axis


![](resources/images/capture-app-analytics-who-item.png)

If any TEI Analytics item has been created, a table will show the item's title and program name, and action buttons to delete or edit that item.

![](resources/images/capture-app-analytics-table.png)

### Home { #capture_app_android_settings_webapp_analytics_home }

Home visualizations are displayed in the home screen (Analytics tab) of the android app.

All items available are first created in the Data visualizer or Line Listing app in DHIS2 and configured in the Android Settings app.

> **Note:**
>
> Visualization items can be sourced either from the **Data Visualizer** or the **Line Listing** app. 
> 
> When choosing a visualization type, the items shown automatically change; if "Data Visualization" is selected, only visualizations created in the Data Visualization app will be displayed. 
> 
> When selecting "Event Visualization" (**v2.4**), only elements created in the Line Listing app will appear in the Visualization search box.
>

To create a **Home** item:

1. Click on "Add Home Visualization" Button.
2. Choose a "Visualization Type" (**v2.4**)
3. Click on the search box and select the visualization from the list or type the name of the visualization item.
4. Add an alternative title, otherwise, the app will display the name of the visualization.
5. By default, the app will enable the group visualization setting.
   1. Create a new group: A free text box will pop up to type the name or
   2. Select a created group visualization: Choose an option from the list to add the visualization or
   3. Disable the group visualization by clicking on the checkbox.
6. Click on the "Save" button.

![](resources/images/capture-app-analytics-home-newGroup.png)

![](resources/images/capture-app-analytics-home-createdGroup.png)

> **Note:**
>
> Visualizations that are added with no group selected, will be displayed in a common "group"
>
> ![](resources/images/capture-app-analytics-default-group.png)
>

To edit the title of a **Home** item (**v2.2.1**):

1. Search for the item by expanding the groups.
2. Click the "Edit" button next to the item's name.
3. A pop-up with only the visualization title available will be available, the other fields will be disabled. If wanted change the visualization title.
4. Click on the "Save" button.

![](resources/images/capture-app-analytics-home-editVisualization.png)


To remove a **Home** item:

1. Search for the item by expanding the groups
2. Click the "Delete" button next to the item's name
3. Click on "Delete"
4. Click on the "Save" button

![](resources/images/capture-app-analytics-home-deleteVisualization.png)

To reorganize a **Home** item inside a group (**New 2.4.2**):

1. Search for the item by expanding the groups
2. Click on the "Up" or "Down" arrow button next to the item's name
3. Keep clicking on the button until the item is in the wanted position 
4. Click on the "Save" button

![](resources/images/capture-app-analytics-home-reorganizeVisualization.png)

To remove a **Home** group:

1. Search for the specific group to delete
2. Click on "Delete Group"
3. Click on "Delete"
4. Click on the "Save" button

All the items associated to that group will be deleted

![](resources/images/capture-app-analytics-home-deleteGroup.png)

To reset all values:

1. Click on "Reset all values to default"
2. Click on the "Save" button

### Program { #capture_app_android_settings_webapp_analytics_program }

Program visualizations are displayed in the search screen (Analytics tab) in tracker programs or in the list screen (Analytics tab) in event programs of the android app.

All items available are first created in the Data visualizer or Line Listing (**v2.4**) app in DHIS2 and configured in the Android Settings app.

> **Note:**
>
> Visualization items can be sourced either from the **Data Visualizer** or the **Line Listing** app.
>
> When choosing a visualization type, the items shown automatically change; if "Data Visualization" is selected, only visualizations created in the Data Visualization app will be displayed.
>
> When selecting "Event Visualization" (**v2.4**), only elements created in the Line Listing app will appear in the Visualization search box.
>
> ![](resources/images/capture-app-analytics-program-visualization-type.png)
> 

To create a **Program** item:

1. Click on "Add Program Visualization" Button.
2. Choose a Visualization Type (**v2.4**).
3. Select a Program.
4. Click on the search box and select the visualization from the list or type the name of the visualization item.
5. Add an alternative title, otherwise, the app will display the name of the visualization
6. By default, the app will enable the group visualization setting.
   1. Create a new group: A free text box will pop up to type the name or
   2. Select a created group visualization: Choose an option from the list to add the visualization or
   3. Disable the group visualization by clicking on the checkbox.
7. Click on the "Save" button.

![](resources/images/capture-app-analytics-program-add.png)

To edit the title of a **Program** item (**v2.2.1**):

1. Search for the item by expanding the groups.
2. Click the "Edit" button next to the item's name.
3. A pop-up with only the visualization title available will be available, the other fields will be disabled. If wanted change the visualization title.
4. Click on the "Save" button.

![](resources/images/capture-app-analytics-program-editVisualization.png)

To remove a **Program** item:

1. Search for the item by expanding the program and group
2. Click the "Delete" button next to the item's name
3. Click on "Delete"
4. Click on the "Save" button

![](resources/images/capture-app-analytics-program-deleteVisualization.png)

To reorganize a **Program** item inside a group (**New 2.4.2**):

1. Search for the item by expanding the program and groups
2. Click on the "Up" or "Down" arrow button next to the item's name
3. Keep clicking on the button until the item is in the wanted position
4. Click on the "Save" button

![](resources/images/capture-app-analytics-program-reorganizeVisualization.png)

To remove a **Program** group:

1. Search for the specific group to delete in the corresponding program
2. Click on "Delete Group"
3. Click on "Delete"
4. Click on the "Save" button

All the items associated to that group will be deleted

![](resources/images/capture-app-analytics-program-deleteGroup.png)

To reset all values:

1. Click on "Reset all values to default"
2. Click on the "Save" button

### Data Set { #capture_app_android_settings_webapp_analytics_data }

Data Set visualizations are displayed in the list screen (Analytics tab) in a Data Set of the android app.

All items available are first created in the Data visualizer app in DHIS2 and configured in the android settings app.

To create a **Data Set** item:

1. Click on "Add Data Set Visualization"
2. Select a Data Set
3. Click on the search box and select the visualization from the list or type the name of the visualization item.
4. Add an alternative title, otherwise, the app will display the name of the visualization
5. By default, the app will enable the group visualization setting.
   1. Create a new group: A free text box will pop up to type the name or
   2. Select a created group visualization: Choose an option from the list to add the visualization or
   3. Disable the group visualization by clicking on the checkbox.
6. Click on the "Save" button.

![](resources/images/capture-app-analytics-dataset-add.png)

To edit the title of a **Data set** item (**v2.2.1**):

1. Search for the item by expanding the groups.
2. Click the "Edit" button next to the item's name.
3. A pop-up with only the visualization title available will be available, the other fields will be disabled. If wanted change the visualization title.
4. Click on the "Save" button.

![](resources/images/capture-app-analytics-dataset-editVisualization.png)

To remove a **Data Set** item:

1. Search for the item by expanding the Data Set and group
2. Click the "Delete" button next to the item's name
3. Click on "Delete"
4. Click on the "Save" button

![](resources/images/capture-app-analytics-dataset-deleteVisualization.png)

To reorganize a **Data Set** item inside a group (**New 2.4.2**):

1. Search for the item by expanding the Data Set and groups
2. Click on the "Up" or "Down" arrow button next to the item's name
3. Keep clicking on the button until the item is in the wanted position
4. Click on the "Save" button

![](resources/images/capture-app-analytics-dataset-reorganizeVisualization.png)

To remove a **Data Set** group:

1. Search for the specific group to delete in the corresponding Data Set
2. Click on "Delete Group"
3. Click on "Delete"
4. Click on the "Save" button

All the items associated to that group will be deleted

![](resources/images/capture-app-analytics-dataset-deleteGroup.png)

To reset all values:

1. Click on "Reset all values to default"
2. Click on the "Save" button

### Visualization user test { #capture_app_android_settings_webapp_analytics_visualization_user_test }

The visualization user test is a feature available in Home, Program and Data Set Analytic setting that helps the admin user to identify if any particular user will be able to see the visualization.

The android settings app checks for at least one of these three permissions:

1. Visualization is public
2. User has individual access to the visualization
3. User is in a group that has access to the visualization

To run the test:

1. Select the user from the list
2. Click on "Run test"

![](resources/images/capture-app-analytics-usertest-access.png)

![](resources/images/capture-app-analytics-usertest-access-visualization.png)

![](resources/images/capture-app-analytics-usertest-noaccess.png)

![](resources/images/capture-app-analytics-usertest-noaccess-visualization.png)

### Analytics Limitations { #capture_app_android_settings_analytics_limitations }

Since the aggregations and calculations displayed are calculated in the device, the implementation of analytics is limited compared to web. 

In summary the compatible and supported objects and features for Data Visualizations are:

- Well-formed analytic objects (series, categories, filters)
- Use of relative periods (Fix periods are not supported)
- User has view access
- Limitations for Pivot Tables
  - Number of header lines: 1 or 2 (*v2.3*)
  - Number of header columns: 2
- Limitations for Charts
  - Number of Series: No limit (but remember you are rendering in a small screen)
  - Number of Categories (doesn't apply for pie chart): No limit

There are many more restrictions which apply to Android Analytics regarding the many configuration options available in the Web Visualizer as well as the supported functions and calculations related to indicators and program indicators. [This table](https://docs.google.com/spreadsheets/d/1127cz7M0K4fux5CU0V54V2Z77NZWCr0BTrZ6jcCec4Q) summarises all supported features.

In the same way, Event visualizations are considered valid if:

- Visualization was created using Line Listing app
- Visualization type is Line List
- Use of relative periods
- Limitations for Table
  - Number of columns: 15


> **Note (v2.2.1)**
>
> When searching for a visualization to add as part of the Analytics visualizations, all visualizations will be listed, but visualizations that don't meet the above restrictions will be disabled. 
>
> ![](resources/images/capture-app-analytics-visualization-search.png)
>

## Custom Intents (New 3.3.0) { #capture_app_android_settings_webapp_custom_intents }

By configuring custom intents, administrators can enable the Android app to launch external applications, send data to them, and receive data back to populate fields automatically.

### Adding a Custom Intent { #capture_app_android_settings_webapp_custom_intents_configuration_adding }

To add a new Custom Intent:

1. Open the Android Settings Web App
2. Navigate to the Custom Intents section
3. Click on **Add Custom Intent**
4. Fill in the configuration parameters as described below

![](resources/images/capture-app-image365.png)
![](resources/images/capture-app-image361.png)

### Configuration Parameters { #capture_app_custom_intents_configuration_parameters }

#### Basic Information { #capture_app_android_settings_webapp_custom_intents_configuration_basic }

Intent Name
:   A unique, descriptive name for the custom intent. This name helps identify the intent in the configuration interface.

Intent Description
:   A detailed description of what the custom intent does and which third-party app it integrates with. This helps other administrators understand the purpose of the intent.

#### Element Binding { #capture_app_android_settings_webapp_custom_intents_configuration_binding }

Element Type
:   Specifies where the custom intent will be attached. Options include:
    
    - **Tracked Entity Attribute**: Links the intent to a specific tracked entity attribute
    - **Data Element**: Links the intent to a specific data element

Attribute/Data Element
:   Select the specific tracked entity attribute or data element that will trigger the custom intent. When a custom intent is configured for a field, users must use the third-party application to enter or search data for that field. Manual data entry will not be available.

> **Note**
>
> Only Data Elements or Tracked Entity Attributes with **TEXT** or **LONG_TEXT** value types are currently supported for custom intents.

Screen/Action
:   Defines where in the Android app the custom intent will be triggered. Available options:
    
    - **SEARCH**: The intent will be available during search operations, allowing users to search for tracked entity instances using data from external apps
    - **DATA_ENTRY**: The intent will be available during data entry, allowing users to populate fields with data from external apps

#### Third-Party Application { #capture_app_android_settings_webapp_custom_intents_configuration_app }

Package Name
:   The complete package name and action of the third-party Android application to launch. This should include both the package identifier and the specific action.
    
    Format: `com.apppackageName.id.CAPTURE`
    
    Example: `com.google.zxing.client.android.SCAN` for a barcode scanner app

> **Important**
>
> The third-party application must be installed on the Android device for the custom intent to work. If the app is not installed, users will receive an error message when attempting to trigger the intent.

### Request Configuration { #capture_app_android_settings_webapp_custom_intents_configuration_request }

The Request section defines the parameters that will be sent to the third-party application when the intent is launched. This allows you to customize the behavior of the external app based on your requirements.

#### Request Parameters { #capture_app_android_settings_webapp_custom_intents_configuration_request_params }

Request Parameters
:   A list of key-value pairs that will be sent as extras to the third-party application's intent. Each parameter consists of:
    
    - **Key**: The parameter name expected by the third-party application
    - **Value**: The parameter value to send
    
> **Note**
>
> Request parameters are type-safe. Follow these formatting rules:
> - **Strings**: Must be surrounded by single quotes (e.g., `'QRCODE'`, `'portrait'`)
> - **Integers**: No quotes needed (e.g., `100`, `640`)
> - **Floats**: No quotes needed (e.g., `3.14`, `2.5`)
> - **Booleans**: No quotes needed (e.g., `true`, `false`)

**Example Request Parameters:**

| Key          | Value       | Description                   |
|--------------|-------------|-------------------------------|
| PROJECT_ID   | 'sample_id' | Id needed for third party app |
| ORIENTATION  | 'portrait'  | Set camera orientation        |
| TIMEOUT      | 30000       | Set timeout in milliseconds   |
| ENABLE_FLASH | true        | Enable camera flash           |

![](resources/images/capture-app-image360.png)

### Response Configuration { #capture_app_android_settings_webapp_custom_intents_configuration_response }

The Response section defines how to extract and process data returned from the third-party application. This determines which value will be populated in the linked tracked entity attribute or data element.

#### Response Parameters { #capture_app_android_settings_webapp_custom_intents_configuration_response_params }

Extra Name
:   The exact name of the extra field in the intent returned by the third-party application. This is the key used by the external app to send data back to DHIS2.
    
    Example: `SCAN_RESULT`, `LATITUDE`, `BARCODE_VALUE`

Extra Type
:   The data type of the returned value. Available options:
    
    - **String**: Plain text value
    - **Integer**: Whole number value
    - **Float**: Decimal number value
    - **Boolean**: True/false value
    - **JSON Object**: A single JSON object
    - **List of JSON Objects**: An array of JSON objects

Property in JSON Object
:   *Only applicable when Extra Type is "JSON Object" or "List of JSON Objects"*
    
    Specifies the property name to extract from the JSON object(s). This should be a direct property of the JSON object.
    
    Example: `value`, `latitude`, `name`

> **Note**
>
> - Only direct properties are supported. Nested properties (e.g., `location.coordinates.latitude`) are not currently supported.
> - Array indexing (e.g., `results[0].name`) is not currently supported.
> - When using **List of JSON Objects** as the Extra Type:
>   - For **SEARCH**: The specified property will be extracted from all objects in the list, allowing users to search for tracked entity instances that match any value in the list.
>   - For **DATA_ENTRY**: The values will be extracted from all objects and concatenated into a single string separated by commas (e.g., `value1,value2,value3`).

![](resources/images/capture-app-image362.png)

### Use Cases and Examples { #capture_app_android_settings_webapp_custom_intents_examples }

#### Example 1: Barcode Scanner Integration { #capture_app_android_settings_webapp_custom_intents_examples_barcode }

This example shows how to integrate a barcode scanner app to populate a patient ID field.

**Configuration:**
- **Intent Name**: Barcode Scanner for Patient ID
- **Intent Description**: Scans patient ID barcodes using ZXing scanner
- **Element Type**: Tracked Entity Attribute
- **Attribute**: Patient ID
- **Screen/Action**: DATA_ENTRY
- **Package Name**: `com.google.zxing.client.android.SCAN`

**Request Parameters:**
| Key | Value |
|-----|-------|
| SCAN_MODE | 'QR_CODE_MODE' |
| PROMPT_MESSAGE | 'Scan patient ID barcode' |

**Response:**
- **Extra Name**: `SCAN_RESULT`
- **Extra Type**: String
- **Property in JSON Object**: *(leave empty for string type)*

#### Example 2: GPS Coordinates Integration { #capture_app_android_settings_webapp_custom_intents_examples_gps }

This example demonstrates capturing GPS coordinates from a mapping application that returns JSON data.

**Configuration:**
- **Intent Name**: GPS Location Capture
- **Intent Description**: Captures GPS coordinates from mapping app
- **Element Type**: Data Element
- **Data Element**: Household Location
- **Screen/Action**: DATA_ENTRY
- **Package Name**: `com.example.gpsapp.CAPTURE_LOCATION`

**Request Parameters:**
| Key | Value |
|-----|-------|
| ACCURACY | 'HIGH' |
| TIMEOUT | 60000 |

**Response:**
- **Extra Name**: `LOCATION_DATA`
- **Extra Type**: JSON Object
- **Property in JSON Object**: `coordinates.latitude`

**Example JSON response:**
```json
{
  "coordinates": {
    "latitude": -1.2921,
    "longitude": 36.8219
  },
  "accuracy": 5.0,
  "timestamp": "2025-11-03T10:30:00Z"
}
```

#### Example 3: Custom Data Collection Tool { #capture_app_android_settings_webapp_custom_intents_examples_custom }

This example shows integration with a custom medical device app that returns multiple measurements in a JSON array.

**Configuration:**
- **Intent Name**: Blood Pressure Monitor
- **Intent Description**: Captures blood pressure from external monitor device
- **Element Type**: Data Element
- **Data Element**: Systolic Pressure
- **Screen/Action**: DATA_ENTRY
- **Package Name**: `com.medical.bpmonitor.MEASURE`

**Request Parameters:**
| Key | Value |
|-----|-------|
| MEASUREMENT_TYPE | 'BLOOD_PRESSURE' |
| UNIT | 'mmHg' |

**Response:**
- **Extra Name**: `MEASUREMENTS`
- **Extra Type**: List of JSON Objects
- **Property in JSON Object**: `systolic`

**Example JSON response:**
```json
[
  {
    "systolic": 120,
    "diastolic": 80,
    "pulse": 72,
    "timestamp": "2025-11-03T10:30:00Z"
  }
]
```
### Limitations and Considerations { #capture_app_android_settings_webapp_custom_intents_limitations }

#### Third-Party App Requirements { #capture_app_custom_intents_limitations_app }

- The third-party application must be installed on all Android devices that will use the custom intent
- The third-party app must support Android Intent-based communication
- The package name and action must be correctly configured and match the third-party app's implementation

#### Data Type Compatibility { #capture_app_android_settings_webapp_custom_intents_limitations_datatype }

- The Extra Type configured in the response must match the actual data type returned by the third-party application
- The tracked entity attribute or data element value type should be compatible with the returned data
- Type mismatches may result in errors or unexpected behavior

#### Device Compatibility { #capture_app_android_settings_webapp_custom_intents_limitations_device }

- Custom Intents rely on Android's Intent system and are only available on Android devices
- Some third-party apps may have specific Android version requirements
- Testing should be performed on all target device models

#### Security Considerations { #capture_app_android_settings_webapp_custom_intents_limitations_security }

> **Warning**
>
> When configuring custom intents that integrate with third-party applications, consider the following security implications:
> - Data sent to third-party apps may be stored or transmitted according to the third-party app's privacy policy
> - Ensure third-party applications are from trusted sources
> - Review the permissions requested by third-party applications
> - Sensitive health data should only be shared with certified and compliant applications
> - Consider implementing Mobile Device Management (MDM) to control which apps can be installed

#### Network and Offline Behavior { #capture_app_android_settings_webapp_custom_intents_limitations_offline }

- Custom intents work in offline mode as long as the third-party app is installed and doesn't require network connectivity
- Some third-party apps may require internet access to function properly
- Ensure the solution works in the expected connectivity scenarios for your deployment

### Troubleshooting { #capture_app_android_settings_webapp_custom_intents_troubleshooting }

#### Common Issues { #capture_app_android_settings_webapp_custom_intents_troubleshooting_common }

**Issue: Custom intent button doesn't appear**
- Verify that the custom intent is correctly configured in the Android Settings Web App
- Check that the device has synchronized the latest configuration
- Ensure you're viewing the correct tracked entity attribute or data element

**Issue: "Application not found" error**
- The third-party application is not installed on the device
- The package name is incorrectly configured
- The third-party app doesn't support the specified action

**Issue: No data is returned**
- Verify the Extra Name matches the key used by the third-party app
- Check that the Extra Type is correct
- Review the third-party app's documentation for the expected response format

**Issue: Wrong value is populated**
- Verify the Property in JSON Object path is correct
- Check that the JSON structure matches the expected format
- Ensure the Extra Type matches the actual returned data type

**Issue: App crashes when launching intent**
- Review the request parameters for syntax errors (e.g., missing quotes for strings)
- Verify the third-party app supports the configured parameters
- Check Android logs for detailed error messages

#### Testing Custom Intents { #capture_app_android_settings_webapp_custom_intents_troubleshooting_testing }

Before deploying custom intents to production:

1. Test with a small group of users on various device models
2. Verify the third-party app is available and properly licensed
3. Test both online and offline scenarios
4. Verify data validation rules are applied to returned values
5. Test error handling when the third-party app is not installed
6. Document the configuration and user instructions

> **Note**
>
> Consider creating a test program or data set specifically for testing custom intent configurations before deploying to production programs.

### Best Practices { #capture_app_custom_intents_best_practices }

1. **Clear Naming**: Use descriptive intent names that clearly indicate the purpose and third-party app being used

2. **Documentation**: Maintain documentation of all configured custom intents, including the required third-party apps and their versions

3. **User Training**: Provide clear instructions to users on how to use custom intents and what to expect. Ensure users understand that manual data entry will not be available for fields with custom intents configured.

4. **App Distribution**: Use Mobile Device Management (MDM) to ensure third-party apps are properly installed and updated on all devices

5. **Testing**: Thoroughly test custom intents in a non-production environment before deployment

6. **Validation**: Implement appropriate validation rules on fields that use custom intents to ensure data quality

7. **Reliability**: Ensure the third-party application is stable and reliable, as it will be the only way to populate the configured field. Have a contingency plan if the third-party app becomes unavailable.

8. **Version Control**: Keep track of third-party app versions and test compatibility when apps are updated

9. **Privacy Compliance**: Ensure custom intent configurations comply with data privacy regulations (GDPR, HIPAA, etc.)

## Installation { #capture_app_android_settings_webapp_installation }

A user can easily install the Android Settings Web App by logging into the DHIS2 and going to **App Management**.

- Click on **App Hub**
- Go to *Android Settings App*
- Click on *Install V2.X.X*

![](resources/images/capture-app-app-hub-install.png)
![](resources/images/capture-app-app-hub-install-webapp.png)


## Log in and first time setup { #capture_app_android_settings_webapp_login }

After a user installs and launches the Android Settings Web App for the first time, the web app will require setting and saving the default values of the configuration. This will apply default settings to all android devices connected to the instance. 

![](resources/images/capture-app-first-time-setup.png){width=50%}

> **Warning**
>
> Be aware that previous versions are deprecated, so you will start with a new default configuration.

![](resources/images/capture-app-first-setup-with-deprecation-message.png){width=50%}

> **Warning (v2.3)** 
>
> When using DHIS2 version equal to or higher to 2.40, only users with "M_androidsettingsapp" or "ALL" authority can *save or update* the configuration, but any user will have *view* access once it is created.
> 


![](resources/images/capture-app-first-setup-no-authorities.png){width=50%}


## Enter and save configuration parameters { #capture_app_android_settings_webapp_enter_and_save }

### Datastore { #capture_app_android_settings_webapp_datastore }

Internally all settings are stored in [Datastore](https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-240/data-store.html) in JSON format.

Datastore structure:

| Item      | Description                                 | Data type |
|-----------|---------------------------------------------|-----------|
| Namespace | Namespace for organization of entries       | String    |
| Key       | Key for identification of values            | String    |
| Value     | Value holding the information for the entry | JSON      |

### Save configuration parameters { #capture_app_android_settings_webapp_save_config }

At the form footer of all settings sections, admin users can find a *Save* button.

![](resources/images/capture-app-save_button.png)

Only when an admin user clicks on this button, all changes made on the current section are saved on the Datastore. These changes will apply to the Android Capture App when they synchronize their configuration.
 
Unsaved changes
:	In case an admin user wants to go to another section when there are still some unsaved changes, an alert will be displayed before navigating away from the current section. In case the user accepts leaving the page, the unsaved changes will be lost.

![](resources/images/capture-app-unsaved-changes.png)
 
#### Reset all values to default { #capture_app_android_settings_webapp_reset_all }

An admin user can restore the settings at any time. There is a *Reset all values to default* button at the form footer of all settings sections. 

![](resources/images/capture-app-reset-default.png)

The default values will be only restored on Datastore and applied after clicking on *Save*. 


## Uninstall the app { #capture_app_android_settings_webapp_uninstall_app }

In case of needing to uninstall the Android Settings App it is recommended to also delete all the data from the reserved datastore namespace.

#### Delete data { #capture_app_android_settings_webapp_delete_data }

- Go to *General* section
- Click on *Disable all settings*
- A modal will pop up, click on *Disable*

![](resources/images/capture-app-unistall-delete-namespace.png)

![](resources/images/capture-app-unistall-delete-namespace-modal.png)

#### Uninstall app { #capture_app_android_settings_webapp_uninstall_app }

- Go to **App Management**
- Click on **Custom Apps**
- Go to *Android Settings App*
- Click on *Uninstall V2.X.X*

![](resources/images/capture-app-unistall-custom-app.png)

![](resources/images/capture-app-unistall-aswa.png)

> **Warning**
>
> This is a critical action, be aware that by doing this, all previous configurations will be permanently deleted.
>


## App Compatibility { #capture_app_android_settings_webapp_app_compatibility }

A label is displayed to indicate the minimum Android app version required to use specific features or functionalities. This ensures that users are informed about compatibility requirements and can update their app if necessary to meet the minimum version.

For example, if a feature requires Android app version 2.9 or higher, the label will show the required version clearly for the user.

![](resources/images/capture-app-aswa-compatibility.png)

[This table](https://docs.google.com/spreadsheets/d/1HZv4iYD9_UVbMAxEgIHYXD_peK_ppzpJLo85MojNmMQ/edit?usp=sharing) summarises all supported features and the compatibility of them with the Android Capture app.