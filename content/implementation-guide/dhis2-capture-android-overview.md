# DHIS2 Capture Android overview { #implementation_guide_overview }

This document focuses on mobile implementations which use the DHIS2 Capture Android App. To get additional information about the different DHIS2 Android apps please visit the [DHIS2 Downloads page](https://www.dhis2.org/downloads) and the [Documentation](https://docs.dhis2.org/en/home.html) on the website. The previous set of DHIS2 Android Apps developed are deprecated but still can be downloaded via the following links:

* Dashboard App (deprecated since March 2020)
    * [Google Play](https://play.google.com/store/apps/details?id=org.hisp.dhis.android.dashboard)
	* [Github](https://github.com/dhis2/dhis2-android-dashboard)
* Tracker and Event App (deprecated since June 2020)
    * [Google Play Tacker](https://play.google.com/store/apps/details?id=org.hisp.dhis.android.trackercapture)
	* [Google Play Event](https://play.google.com/store/apps/details?id=org.hisp.dhis.android.eventcapture)
	* [Github Tracker](https://github.com/dhis2/dhis2-android-trackercapture)
	* [Github Event](https://github.com/dhis2/dhis2-android-eventcapture)
* Data Capture App (deprecated since September 2020)
    * Google Play (link currently not available)
	* [Github](https://github.com/dhis2/dhis2-android-datacapture)

The DHIS2 Capture Android App allows offline data capture across all DHIS2 data models. Data and metadata are automaticall synchronized whenever there is Internet access, always keeping the most relevant data for the logged user in the local device.

## Easier Login and enhanced data protection { #implementation_guide_overview_easier }

Server URL can be set via a QR code. The app will also remember previously used URLs and user names. Once a user is logged, a four digit PIN can used to secure the app with a soft log out.

## Configurable App theme and Icon { #implementation_guide_overview_configurable }

The appearance of the app, including icon and color is determined by your server configuration. You can create a shortcut to the app with your institutional logo in the home screen of the mobile device by using the App Widget.

![](resources/images/implementation-guide-login.png){ .center width=25% }

## Attractive, user friendly navigation { #implementation_guide_overview_attractive }

All programs and datasets accessible to the logged user are integrated into the home screen. Each program or dataset will be displayed with their associated icon and colour.

![](resources/images/implementation-guide-user-friendly.png){ .center width=25% }

## Fully functional while offline: intelligent sync { #implementation_guide_overview_fully_functional }

A local database in the mobile device keeps a synchronized copy of the DHIS2 programs and datasets available to the logged user. The most relevant data is also automatically synchronized.

* Tracked Entities: by default, up to 500 active enrolments, prioritizing the most recently updated on the user’s assigned data capture Org Unit(s).
* Events & Datasets: by default, the most recent 1,000 events or 500 datasets.

> **Note**
> These parameters are configurable via the specific menu in the App or generally at server level using the [DHIS2](https://apps.dhis2.org/app/a1bd6b5b-de8c-4998-8d34-56c18a139683)

## Tracker dashboard { #implementation_guide_overview_tracker_dashboard }

DHIS2’s powerful tracker data model has been fully implemented in the small screen. The tracker dashboard incorporates feedback, relationships, indicators and notes.

The app implements tracker logic by supporting most program rules, giving the possibility to add, schedule or refer new events, depending on the server configuration.

![](resources/images/implementation-guide-tracker-search.png){ .center width=25% }

## Integrated search for tracker { #implementation_guide_overview_integrated_search }

Before being able to add a new tracked entity, the app requires the user to perform a search. If offline, the search is performed on the local database, and when online, it will suggest records for download, based on user’s organization unit search configuration. This functionality minimized potential duplicates, even when the user is offline.

## Pictorial Data Entry { #implementation_guide_overview_pictorial }


Data Entry comes to life - icons and colors can be used to illustrate questions’ answers. Available for data elements with associated options sets in both, single event and tracker programs.

![](resources/images/implementation-guide-pictorial-entry.png){ .center width=25% }

## Event Completeness { #implementation_guide_overview_event_completeness }

During data entry, the app will display information about the current status of completion for a program stage. Useful for complex surveys with multiple sections.
