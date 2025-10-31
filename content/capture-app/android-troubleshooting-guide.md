# Android Troubleshooting guide { #capture_app_troubleshooting_guide }

## Purpose { #capture_app_troubleshooting_guide_purpose }

This guide follows the journey of a DHIS2 Android user and implementer, from setup to field data collection, synchronization, and ongoing maintenance. Each stage explains how some issues may appear, possible causes to them and the fixes using DHIS2’s Android ecosystem tools.

## Setup and Configuration { #capture_app_troubleshooting_guide_setup }

Before any data is captured, the setup determines how synchronization will be. This phase focuses on installation, configuration, and first sync.

### Sync Mechanism { #capture_app_troubleshooting_guide_sync }
The Android Capture app synchronizes two distinct data streams:

**Metadata/Configuration**
Metadata includes all structural and configurational information downloaded from the DHIS2 server (programs, data sets, categories, category options, org units, option sets, program rules...). The Android app stores this information in its local database so that users can continue to operate even when offline.

Metadata synchronization ensures that devices have the latest configuration from the server. The admin defines how often the device should check for updates using the Android Settings web app. Metadata sync can occur every 1 day, 1 week, or manually (Daily set as default).

In upcoming DHIS2 versions, shorter periods (such as 6 hours and 12 hours) will be available, giving administrators finer control. 

Frequent metadata syncs can be useful during rollout or configuration changes, while weekly syncs reduce bandwidth use in stable deployments.

**Data**
Data refers to everything the user captures through the Android Capture app (tracked entity instances, enrollments, events, and data values). The app keeps this data locally until a successful upload occurs. Data synchronization can be scheduled at intervals of 30 minutes, 1 hour, 6 hours, 12 hours, 1 day, or can be done manually. The best setting depends on network quality: frequent syncs for areas with stable connectivity, daily syncs for remote regions.

The offline first design of DHIS2 Android means that users can always work without a connection. When network access returns, queued data is sent automatically or manually, depending on the configuration. 

Because of this, maintaining fresh metadata and appropriate sync scope is critical to avoid conflicts between the device and server.

### Sync Scope and File Size Management { #capture_app_troubleshooting_guide_syncscope }

Administrators can define separate download parameters for tracked entity programs (Tracker) and event programs. The app always prioritizes program-specific configurations before applying global defaults. For instance, if a device is set to download 1000 tracked entities globally but a specific program limit is defined for 200, the app first counts those 200 and then subtracts them from the total global limit. 

Event settings only apply to event-type programs, tracker programs are governed by tracked entity download limits. This ensures that devices do not exceed their capacity and that key programs always receive priority data.

The app can also respect a maximum download file size (set in Android Settings). Files larger than this limit won’t be downloaded by the app. This prevents devices with low memory or poor connectivity from downloading very large files.

#### Reserved Values { #capture_app_troubleshooting_guide_reserved_values }

Reserved values are pre-generated unique identifiers used for tracked entity attributes marked as auto-generated (for example, patient or case IDs). When a user registers a new tracked entity, the app assigns one of these reserved IDs locally, ensuring that even offline registrations have globally unique identifiers.

Here’s how the process works:

The server pre-generates a pool of unique IDs for each auto-generated attribute (configurable in ASWA, 500 by default).

During metadata/configuration sync, the device downloads this pool.

Each time a new tracked entity is registered, one reserved value is consumed.

 When the pool is used to a certain degree, a new batch is requested on the next successful sync. This refill can also be done manually by the user in the app settings menu.

### Tracker Importer and Exporter – Impact on Synchronization { #capture_app_troubleshooting_guide_tracker_importer }

The Tracker Importer and Tracker Exporter are key backend services in the DHIS2 ecosystem that directly influence how the Android Capture app uploads data and how much data it downloads.orks

The DHIS2 **Tracker Importer** validates uploads of tracked entity instances, enrollments, events, and relationships against the server’s metadata (mandatory attributes, program rules, ownership and sharing, and organisation-unit capture). When a device reconnects and syncs, its payload is submitted to the importer; if validation succeeds the data is committed, and if not, the importer returns a detailed summary shown on the device and in the [Synchronization Troubleshooting app](https://docs.dhis2.org/en/use/android-app/android-web-apps/synchronization-troubleshooting.html).

The **Tracker Exporter** determines which tracked entities, enrollments, and events the device can download during sync, based on the user’s organisation units, assigned programs, and the Android sync scope. If the exporter returns an overly large result, first syncs become slow and may hit device limits;.

The Android Capture app enabled these services progressively. Use this matrix when aligning devices with your server:

|Service|Android support status|
|-|-|
|Tracker Importer|Available from DHIS2 2.38+ <br> Default from 2.40+ <br> Mandatory from v43+|
|Tracker Exporter|Available from 2.40+ <br> Default from 2.40+ <br> Mandatory from v43+|
|||

In earlier server versions (2.36–2.37), the endpoint existed, but the Android app did not use it by default. That was a deliberate safety choice while the endpoint matured. From 2.40 onward, both importer and exporter are the standard path for Android sync, and from v43+ they are required. If your instance is below these thresholds, test behavior in staging before a large rollout.

#### When to use the “New” Tracker Importer endpoint

*Use the new importer when:*

*Your DHIS2 server version is 2.36 or higher.
* You are handling large mobile device uploads or offline-first scenarios.
* You want improved performance, better error summaries, and future-proof architecture.

*You may experience issues if:*

* Metadata on the device is outdated (so the client payload fails validation).
* Export/download queries return large payloads, causing mobile sync delays or timeouts.

### Using the Configuration Troubleshooting Feature (Training App Only) { #capture_app_troubleshooting_guide_config_feature }

The Configuration Troubleshooting feature is a diagnostic tool available only in the DHIS2 Android Training App, not in the production Capture App. It is designed for administrators and implementers to test and validate configuration elements such as program rules and translations during setup or training, before rollout to the field. This tool does not require special user roles or authorities. 

#### Purpose and Use Cases

The Configuration Troubleshooting feature helps identify metadata inconsistencies early, preventing validation or sync errors in production. It allows administrators to:

* **Validate program rules:** The app runs a rule validator that checks all program rules stored locally on the device, highlighting configuration inconsistencies (invalid references, missing fields, or circular dependencies).

* **Test translations:** The app includes a language switcher that allows users to toggle between available interface languages instantly. This helps identify untranslated or mislabeled fields, buttons, and option sets before rollout.

Including this validation step as part of your configuration workflow ensures that production deployments of the Capture App are stable and consistent, minimizing field-level data entry errors caused by configuration mismatches.

### Managing APK Distribution and Version Alignment { #capture_app_troubleshooting_guide_APK_distribution }

Synchronization reliability also depends on maintaining consistent Android Capture versions across all devices. The [APK Distribution](https://docs.dhis2.org/en/use/android-app/android-web-apps/apk-distribution.html)  feature in the web app allows administrators to assign specific app versions to user groups. 

When administrators upload a new Android Capture version, they define the version number, optionally set minimum or recommended Android OS versions, and assign access to specific user groups. Each user group can have access to several versions, but every user will only see the latest version assigned to their group. If no group is assigned to any version, the system defaults to the latest version for all users in the instance.

When a new version is uploaded, Android users will see an update notification the next time they log in or when they check for updates in the app. The message prompts them to download the latest APK directly from the instance, but the update is not mandatory. Users can choose to dismiss the message and continue using their current version. This design ensures that updates can be introduced gradually without interrupting field work or forcing installations during critical activities.

It is important to understand that APK Distribution does not enforce updates or control devices. Its role is limited to displaying update information and facilitating version downloads directly from the DHIS2 server. Administrators remain responsible for coordinating updates and ensuring that users eventually migrate to the recommended version.

### Common Issues During Initial Setup { #capture_app_troubleshooting_guide_common_issues_setup }

During initial setup, most synchronization and configuration problems arise from mismatched user permissions or incomplete metadata sharing. Ensuring proper configuration before users begin data entry is essential for stable synchronization and accurate ownership validation.

The following table summarizes the most common setup problems, their causes, and how to resolve them using DHIS2 tools. Before users begin capturing data, ensure these configuration checks are verified. Most sync or visibility problems stem from one or more of these setup issues.

|Symptom|Root Cause|How to Fix|Tools / Checks|
|-|-|-|-|
|**Programs/Data set not visible after login**|User has capture Org Units but no access to programs/data sets or TETs.|Check that the user group has “Can capture and view” access to both Program and Tracked Entity Type. Re-sync configuration after changing sharing.|Maintenance app → Programs sharings/ OU access → TET sharings|
|**Missing stages**|Program stages not shared consistently.|Re-check that Program Stages inherit the same sharing as their parent program.|Maintenance app|
|**Cannot register new tracked entities (no IDs generated)**|Reserved values exhausted or not downloaded.|Increase reserved value count. Trigger a configuration sync.|Android Settings Web App → Reserved Values|
|**Cannot create new stage or data set period/missing options in category combination**|The Category Combination or its Category Options are not shared with the user, are expired, or are filtered out by period or Org Unit.|Check sharing for all Category Options linked to the program or data set. Ensure options are active and valid for the selected Org Unit and period.|Maintenance app → Category|

## Synchronization and Troubleshooting: When Data Doesn’t Upload { #capture_app_troubleshooting_guide_sync_errors }

Synchronization is where most support questions arise. Once the device reconnects, data collected offline is uploaded through the Tracker Importer, which validates every record against the server’s configuration and permissions. When this process encounters issues, the Android Capture app now provides an improved, user-friendly way to navigate and resolve them.

### Sync Error Navigation in the Android App { #capture_app_troubleshooting_guide_error_navigation }

The Android Capture app presents synchronization errors directly on the sync dialog after each sync attempt. Errors are grouped by program or data set and show a clear message describing what went wrong. The navigation has been redesigned so that the user can tap any listed error and the app automatically opens the corresponding event, enrollment, or data set. From there, the problematic field is highlighted for quick correction.

Once the data is fixed, the user tap the “Refresh” button to retry synchronization immediately. This behavior allows field workers to correct data without searching through multiple forms or stages.

Some of the complex backend error codes are translated into clear sentences to help users understand whether an issue is about permissions, configuration, or data entry.

### Synchronization Troubleshooting App (on the Server)  { #capture_app_troubleshooting_guide_sync_app }

For administrators, the [Synchronization Troubleshooting App](https://docs.dhis2.org/en/use/android-app/android-web-apps/synchronization-troubleshooting.html) in DHIS2 complements what users see on their devices. It provides server-side validation results, showing which payloads were rejected, when, and why. By filtering by message type, the admin can quickly match a device error with its corresponding import summary. This level of traceability is essential for diagnosing whether the problem stems from metadata, ownership, or program rules.

At the moment, the Synchronization Troubleshooting App only stores the errors from the last 24h (they are clean up to save disk space). This is useful to identify and correct ongoing synchronization problems, but it does not allow checking past errors.

This cleanup period is defined in System Settings and applies to all single-run jobs (such as data imports). The value can be changed through the API but no recommended since increasing the period will retain errors for longer but also increase database storage.

### Exporting and Importing the Local Database for Analysis { #capture_app_troubleshooting_guide_export_app }

The Android Capture app includes a powerful diagnostic function that allows implementers to extract or restore the entire local database from a device. This feature is intended when data inconsistencies or synchronization failures cannot be resolved through the usual sync or configuration steps.

When users experience persistent sync issues, administrators can request a copy of the local database to inspect its contents. From the app’s Settings menu, select Export database. The app generates an encrypted file containing all locally stored metadata, configuration, and captured data. This file can be safely shared with the system administrator or support team.

To import a database for review, open the Android Capture app on another device or a testing phone. On the login screen, tap the three-dot menu in the top right corner and select Import database. Choose the previously exported file. 

Once imported, the administrator must use the same user credentials as the original owner to view the data, programs, and configuration stored in that database. This process allows support teams to reproduce the environment exactly as the user experienced it and to identify where synchronization or validation failed.

Exporting and importing local databases provides a secure and realistic way to debug issues that are otherwise hard to trace remotely, especially in large-scale deployments where devices operate offline for extended periods.

### Interpreting and Resolving Common Errors { #capture_app_troubleshooting_guide_common_issues_sync }

The Android app maps DHIS2 Tracker Importer  error patterns to readable messages. Below is a reference of the most common errors, how the app currently interprets them, what they mean, and practical next steps.

| Code | Message Shown in App | Why am I seeing this error? | How to Resolve |
|:----:|:----------------------|:-----------------------------|:----------------|
| **E1000** | You do not have access to %s | You’re creating/updating data in an Organisation Unit you don’t have data capture rights for (or those rights were removed after you captured data offline). | If you DO NOT need to sync this data: On device, delete the local record(s) or Delete local data → Sync configuration so the app refreshes permissions and removes that OU from your scope. <br><br> If you DO need to sync it: Temporarily restore the user’s capture OU and program write sharing → let the user sync successfully → Sync configuration and apply the new, restricted permissions. |
| **E1001** | You do not have access to the type %s | No write access to the tracked entity type used by the program. (or those rights were removed after you captured data offline) | Don’t need the data: Delete the pending registrations using that TET → Sync configuration. <br><br> Need the data: Grant write access to the TET (and program) or let a user with access perform the upload → sync data → then revert permissions and Sync configuration on device. |
| **E1002** | The %s already exist. (%s: %s) | Duplicate tracked entity (same UID) or a unique attribute collision (national ID already used). | Don’t need the data: Remove the duplicate on device → Refresh. <br><br> Need the data: Search the TEI on server → update the existing TEI (if it’s a unique attribute conflict, change the value to the correct, unique one) → re-sync data. |
| **E1003** | %s is outside your search scope | Attempt to access TEI or event in an OU outside user’s search scope. | This might happen when the TEI is transferred from an OU outside the search scope |
| **E1005** | The %s type could not be found | The Tracked Entity Type referenced by the device no longer exists | If record is disposable: Delete it → Sync configuration. <br><br> If you must keep it: Configuration sync on the device → ensure the TET exists and is assigned to the program → retry data sync. |
| **E1006** | The attribute %s does not exist | The payload contains an attribute UID that isn’t on the server (metadata changed since capture). | Discard data: Delete/edit the attribute data → Refresh → Sync configuration. <br><br> Keep data: confirm the attribute is still part of the program/TET → re-enter a valid attribute if it was replaced → Sync configuration → re-sync data. |
| **E1007** | The attribute does not match the value type %s. (Error: %s) | Entered value doesn’t match the attribute’s value type (number vs text, date format, etc.). | Don´t keep data: Remove/clear the invalid value→ Refresh. <br><br> Keep data: Remove the value → Sync Configuration → Correct the value to match the expected type → re-sync data. |
| **E1008** | The program stage %s has no reference to a program. | Broken metadata: the Program Stage lost its parent Program link. | Fix the stage program linkage on server (API, Import/Export app)→ Sync Configuration. |
| **E1009** | The file has already been assigned. | The same file resource was linked twice or reused improperly. |  |
| **E1031** | Event ‘occurredAt’ date is missing. | Occurs when you attempt to import or create an event without specifying the required occurredAt (event date) field. | • If you encounter this error during import (e.g., via CSV or JSON), you must ensure that every event row or object includes a valid occurredAt value. If the field is missing or empty, the import will fail. <br> • If you need to fix existing data in the database, you can use [SQL scripts](https://github.com/dhis2/dhis2-releases/blob/master/releases/2.43/migration-notes.md) to assign a default date or remove inconsistent records. |
| **E1032** | The %s event was not found in the server. | The local record references an event that was deleted or never existed on the server. | Manually delete the event |
| **E1063** | The %s was not found in the server. | The local record references a TEI that isn’t on the server (deleted or never uploaded). | Manually delete the TEI |
| **E1064** | Attribute value %s is not unique. | The unique attribute value is already used by another TEI. |  |
| **E1069** | Program linked to enrollment was not found. | Enrollment references a Program the server doesn’t have (UID changed/removed). |  |
| **E1081** | The enrollment was not found in the server. | The local enrollment was deleted on server or never imported. |  |
| **E1084** | File reference not found. | The file resource UID doesn’t exist on the server (expired, deleted, or never uploaded due to offline capture). |  |
| **E1100** | You do not have the authority to delete the %s. | You tried to delete a TEI without the required authority (cascade delete). | To delete record: Grant temporarily the authority (e.g., F_TEI_CASCADE_DELETE) to perform deletion → Sync data → Sync Metadata. <br><br> To keep the record: Use granular sync to sync the rest of the records → Delete local data → sync configuration → Sync data to restore local DB. |
| **E1103** | You do not have the authority to delete the enrollment. | You tried to delete an enrollment without the required authority. | To delete record: Grant temporarily the authority to perform deletion → Sync metadata → Sync data → Revert change → Sync Metadata. <br><br> To keep the record: Use granular sync to sync the rest of the records → Delete local data → sync configuration → Sync data to restore local DB. |


| Code | Server Message | Likely Cause | Corrective Action |
|:----:|:----------------|:--------------|:------------------|
| **E1010–E1013** | Could not find Program/OU/Stage linked to Event | Deleted or misconfigured program metadata. | Verify linked program and OU; reassign. |
| **E1014–E1016** | Enrollment into a non-registration program or duplicate active enrollment. | Trying to enroll multiple times into a single-enrollment program. | Check program type; close previous enrollment. |
| **E1050–E1057** | Invalid or missing event dates, category options. | Date outside allowed range or invalid category combo. | Adjust event date or category options. |
| **E1068–E1070** | Missing linked entities for enrollment. | Enrollment references nonexistent TEI, program, or OU. | Sync metadata; restore missing entities. |
| **E1076–E1077** | Mandatory data element missing or text exceeds length. | Violates attribute constraints. | Complete missing fields or shorten text values. |
| **E1082–E1083** | Event deleted or user unauthorized to edit. | Trying to modify deleted or completed event. | Unmark as completed or re-create event. |
| **E1085** | Attribute value type mismatch. | Wrong data type entered. | Match expected value type. |
| **E1086–E1089** | Program stage mismatch or missing in enrollment. | Inconsistent program–stage relationship. | Rebuild program rules and sync metadata. |
| **E1090** | Mandatory attribute not declared in TEI type. | Metadata inconsistency. | Add attribute to TEI type. |
| **E1096–E1099** | Missing data read/write access to Program or CategoryOption. | Permissions or sharing issue. | Adjust sharing; verify role configuration. |
| **E1301–E1312** | Generated by program rules — mandatory fields or relationships missing. | Rule hides a required field or missing relationship. | Update rules or data; rerun sync. |
| **E4000–E4018** | Relationship constraint or duplication errors. | Invalid or circular relationship definitions. | Review relationships; ensure TEIs link correctly. |
| **E5000–E5001** | Persistence or delete dependency errors. | Object cannot be deleted due to reference integrity. | Clean dependencies; retry. |
| **E9999** | N/A — placeholder. | Undefined import error. | Check logs or DHIS2 API for details. |


