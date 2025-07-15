# Executive Summary { #implementation_guide_executive }

## Background { #implementation_guide_executive_background }

The DHIS2 Android Capture App is the official mobile application for field-based data entry in DHIS2. It was developed in response to the growing use of smartphones in low-resource settings, particularly in Sub-Saharan Africa, and the dominance of Android as the preferred mobile platform. The application was released in September 2018 by the University of Oslo and builds upon the lessons learned from previous DHIS2 mobile apps, including Data Capture, Tracker Capture, Event Capture, and Dashboard.

The Android App is designed to support both Tracker and Aggregate data entry within a single interface, consolidating the functionality of earlier apps into a more streamlined user experience. Its architecture prioritizes offline functionality, making it a reliable option for frontline health workers and data collectors who work in environments where internet connectivity is limited or inconsistent.

## Purpose of This Guide  { #implementation_guide_purpose}

This guide is  intended to support implementation teams throughout the full lifecycle of a mobile deployment project.  The steps of the deployment, which will be described in detail later in the document, include: 

1. Ensuring security and data protection
2. Evaluating mobile device requirements
3. Installing and setting up the app
4. Performing internal testing and user acceptance testing (UAT)
5. Conducting field testing and piloting
6. Managing training, app distribution, and device logistics
7. Executing a successful scale-up and rollout

It is also included a document map which groups the sections of the document into the phases of a mobile implementation project. All aspects here represented should be considered at the beginning of the project and planned accordingly. This representation illustrates in which phase of the project they will be of critical importance.which summarized its key aspects and facilitates following up this guidelines in your project. It is important to highlight that the *cycle represented in the document map* considers the requirement gathering process finished. The document map can be found in the first section.

In the last section, it is included a checklist which summarized its key aspects and facilitates following up this guidelines in your project.

## Target Audience { #implementation_guide_executive_target_audience }

This guide is intended for:

* Project managers and implementers leading the Android deployment
* Program coordinators and trainers supporting field staff
* Technical teams involved in app setup and customization

While the content is structured for those managing the process, it is recommended that the guide be shared with everyone involved in the rollout to ensure a common understanding of the implementation goals, timelines, and requirements.

## Strategic Importance { #implementation_strategic_importance}

The Android App is not a replacement for the DHIS2 web-based platform but a complementary tool designed for mobile-first contexts. It takes into account the realities of fieldwork — such as small screen sizes and unreliable connectivity — and aims to improve the user experience in those environments.

When properly implemented, the app can support a wide range of health system functions, including client follow-up, routine reporting, and service delivery monitoring. Evidence from past implementations and global studies suggests that mobile tools like this one can improve health worker productivity and enable more responsive decision-making at the point of service. However, for these benefits to be realized, adequate investment in training, supervision, and infrastructure is essential.

## Feature Highlights { #implementation_feature_Highlights}

Understanding the core features of the DHIS2 Android Capture App is essential for planning a successful implementation. This guide focuses on how to prepare, configure, and deploy the app, but knowing what the app can actually do is just as important for making informed decisions around training, rollout, and support.

The Android App includes a set of powerful, field-tested capabilities designed to handle real-world challenges—such as working in areas without connectivity, capturing precise locations, and supporting complex program workflows. Below is a summary of the most relevant features for implementers. For a deeper look at how each feature works in practice, refer to the [DHIS2 Android Use Guide](https://docs.dhis2.org/en/use/android-app/about-this-guide.html).

### Offline-first Design
The app is built to work fully offline. Users can capture data, run validations, apply program rules, and use calculated fields without needing a network connection. Synchronization happens later, when connectivity is available.


### Location and Mapping Support
Field workers can collect geolocation data and work with maps, even when offline.

* GPS coordinates can be captured without internet
* Suitable for outreach, community visits, and location-based services

### Localization and Customization
Programs can be adapted to local needs through language, branding, and configuration.

* Full support for translated program metadata and UI labels
* Custom icons and colors
* Configurable sync settings, program rules, and UI behavior* (Using the Android Settings WebApp)

### Multi-Account and Quick Setup
Designed to scale and simplify management across teams, regions, and servers.

* Support for multiple accounts on a single device
* QR code login for fast setup and onboarding
* Download and sync of metadata tailored to each user
