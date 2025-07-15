# Scale Up { #implementation_guide_scale_up }

## Acquisitions { #implementation_guide_scale_up_acquisitions }

Scaling up a DHIS2 Android implementation is a complex but manageable process that begins after thorough testing and piloting. At this stage, decisions must be made regarding hardware acquisition, app distribution strategy, mobile device management, training programs, and—if relevant—SMS infrastructure. Planning well at this stage ensures stability, sustainability, and user satisfaction as the system is deployed at larger scale.

### Purchasing of devices vs BYOD (bring your own device)

Initially you should buy different devices to allow users to evaluate them and provide you with feedback. Once the device that you will be using is decided upon, you should only buy 10 or less units, or whatever is needed for the testing and the pilot phases. Only when the pilot is coming to completion, you should buy equipment for the next 6 months roll-out. Some very large projects will take years for a national roll-out, and your hardware adquisicion plan should expand across years. Recommendations on the technical specs for devices are in the chapter [Mobile devices specifications](https://docs.dhis2.org/en/implement/android-implementation/mobile-device-specifications.html).

You should consider the feasibility of using a BYOD policy - this format allows users to bring their own devices, as long as they satisfy a minimum technical standard, which you will define for your project. You will normally offer some sort of incentive, likely to be in the form of eCash or airtime. The advantages of this approach are obvious: it avoids the large initial cost for acquisition, as well as it reduces the administration costs and logistics considerations. On the other hand, you will have the challenge of a very heterogeneous hardware environment, meaning different devices and Android OS versions. This mainly affects the debugging process.

### Distribution of the app (now and later)

The DHIS2 Android Capture App is actively maintained, with four releases per year: two regular feature (minor/major) releases, and two patch releases focused on bug fixes and stability improvements. Each version is tested for compatibility with supported DHIS2 server versions and includes detailed release notes.

In addition to these scheduled releases, interim APKs may also be published when new or updated translations are submitted through Transifex. These APKs reflect the latest available language support and are especially valuable for multilingual implementations or training needs in local languages.

The official distribution channels are:

* **Google Play Store:** Recommended for smaller implementations or BYOD scenarios. The app is available at DHIS2 on Play Store. Note that apps installed from the Play Store may auto-update unless this is manually disabled on the device.
* **GitHub Releases:** Every official version is published on [DHIS2 GitHub](https://github.com/dhis2/dhis2-android-capture-app/releases), where you can download the APK files manually. APKs installed this way will not update automatically, which is preferable for implementations requiring version control and pre-release testing.

As an implementer, once your testing and training materials are finalized, it is critical that the app version used during training is frozen and not updated automatically during rollout. New versions can introduce changes in UI, program rule behavior, or compatibility issues with your specific configuration. Each new version should be carefully tested before adoption.

For larger implementations, we recommend:

* Avoiding auto-updates from the Play Store by disabling them on all devices.
* Using a Mobile Device Management (MDM) system or custom APK hosting page to control which version is used and when it is updated.
* Clearly documenting the version and configuration used during training to ensure consistency throughout rollout.

>**Note**
>If MDM tools are not available, alternatives include APK distribution via a secure internal portal, shared folders, or QR-based install links generated during configuration.
>

For detailed guidance on MDM and alternative distribution options, refer to the [Mobile Device Management section.](https://docs.dhis2.org/en/implement/android-implementation/managing-mobile-devices/considerations.html)

#### Alternatives and Complements to MDM: APK Distribution Strategies

If a full MDM setup is not feasible, there are alternative methods to distribute and manage the DHIS2 Android app, depending on the technical capacity of your team and the scale of the implementation.

1. [APK Distribution Web App](https://docs.dhis2.org/en/use/android-app/apk-distribution.html)

To support projects that need controlled rollout without complex infrastructure, the DHIS2 Android team provides an official APK Distribution Web App. This tool allows administrators to host a simple internal or public-facing webpage that shares trusted APK builds.

This method is especially effective when:

* You want to lock the app to a specific version that has been tested and validated.
* Google Play is unreliable or blocked.
* Updates need to be managed manually, not automatically.

The app provides version history, changelogs, and contextual guidance. Devices must allow installations from unknown sources, but this approach is simple to maintain and widely adopted across DHIS2 implementations.

2. Google Play Store (with Caution)

Installing the DHIS2 Android Capture App from the Google Play Store provides convenience, but should be used carefully in structured rollouts. Automatic updates can break compatibility or introduce UI changes unexpectedly. If Play Store is used, configure devices to disable auto-updates for DHIS2, or restrict them via managed Play Store in enterprise setups.

3. F-Droid and Private App Repositories

Some implementers prefer using F-Droid, an open-source Android app repository that allows for hosting private app channels. With F-Droid, you can offer secure, controlled app delivery without relying on commercial app stores. However, it has limitations in bandwidth control and device management.

*Choosing the Right Approach*

Ultimately, the right distribution and device management strategy depends on:

* The number of users and devices.
* Whether devices are owned by the institution or BYOD.
* Network availability.
* Security needs.
* Your internal support capacity.

For smaller rollouts or pilots, a shared APK via a webpage or Google Drive folder might suffice. For national programs, an MDM combined with APK hosting and a robust SOP for app version control is highly recommended.


### Telecommunication contracts

If your installation plans to include the use of SMS for transmitting selected records via SMS when mobile data is not available, you will need to establish a contract with a local aggregator which can provide you with an incoming number to receive the SMS. You should configure your server to receive & send SMSs - please see DHIS 2 developers documentation on [SMS connections](https://developers.dhis2.org/docs/mobile/android-sdk/sms/) . You will need to estimate the number of messages per month to be able to forecast the monthly cost.

The process of selecting and signing a contract with an SMS provider varies by country and it depends on the procurement procedures of your organization.

### Planning large acquisitions { #implementation_guide_scale_up_planning }

Each project will need a mix of device types: phones, tablets, and Chromebooks.  Most mobile devices are likely to be allocated to a dedicated user. Things to consider will include the nature of the job. For example, community workers will use smartphones or tablets. But health workers that work on a facility may prefer a tablet with an external keyboard or a Chromebook. 

The actual large-scale acquisition should be delayed as much as possible. Initially, the recommendation is to purchase as few devices as possible for testing the configuration and given some level of choice to future users. Once a decision to move into a pilot is agreed, the second purchase should ideally be limited to the devices needed for the pilot. If the roll-out plan spans over a year, the acquisition of the devices should also be split across time: better devices at the same price point are constantly being offered by manufacturers on cycles that vary between 12-18 months.

Example of a total acquisition of 100 to 1000 devices.

|Project Month|Phase|Acquisition|# of devices|
|---|---|---|---|
|Month 2|Design and initial configuration|Select 3 or 4 possible form factors. Buy from one or two manufacturer|2-8|
|Month 4-6|Pilot|Buy only the devices required to complete the pilot|10-30|
|Month 6-12|Roll out - phase 1|First mass-acquisition|50-500|
|Month X|Roll out Phase X|-->|50-500|
|Month 36-48|Upgrade replacement|Replace devices|X|

## Mobile Device Management { #implementation_guide_scale_up_mdm }


Mobile Device Management refers to software used for the administration of mobile devices. You will need an MDM software when you have to support hundreds of devices and it becomes necessary to control the apk file distribution across the devices, provide tech support and enforce institutional policies. Most options are offered as monthly-fee services. Some free apps offer kiosk mode, but charge a monthly fee for basic remote management.

The desirable features of an MDM software can be classified as basic and advanced. Here is a list of the desirable features:

- Basic features:
  - Require a screen lock password
  - Provision of authorized apps
  - Lock devices and wipe information if they’re lost or stolen
  - Control the upgrade of the Android App
  - Enforce backup policies
- Advanced features:
  - Enforce password strength policies
  - Enforce network usage policies
  - Track device location
  - Restrict access to settings and features (example - wifi/network, screen capture)

When deciding which is the best MDM software for your needs you should try to answer the following questions:

- How many devices do I need to manage?
- How often do I have physical access to the device?
- Which features do I really need?
- Which policies do I have to implement
- How hard will it be to install and maintain
- How will it affect the user experience?
- Do we need to allow BYO? (Bring Your Own Device).
- How will it affect the device?

In the next page you can find a list of available MDM software (please keep in mind that prices and conditions will change over time).

- Mobilock Free (unable to update software)
- SOTI (MobiControl) (can be expensive - $2.20/device/month)
- Miradore (no remote support)
- Applock (unable to control software update )
- AcDisplay (unable to control software update )
- F-Droid (unable to limit data consumption)
- APPDroid (unable to limit data consumption)
- Master List (unable to control software update )
- Firebase (unable to limit data consumption)
- Intunes (users need to be part of a MS Office 365 deployment)
- MobileIron (can be expensive - 3.15 USD /device/month \+ 2.368 USD for deployment)
- IBM Maas360 (too expensive - 1.60 USD /device/month \+ 0.50 USD /device/month for remote support, for 3.000 devices)
- AirWatch (unresponsive and can be expensive - 3.80 USD /device/month for 3,000 devices for 3 years)
- XenMobile (Citrix) (can be expensive - 2.03 USD /device/month for 3,000 devices)
- Good for Enterprise (Blackberry) (can be expensive - 2 USD /device/month \+ 2.5K USD for deployment)

> **Note**
>
> Check the specific [Mobile Device Management Guideline](https://docs.dhis2.org/en/implement/android-implementation/managing-mobile-devices/considerations.html) for more information about this topic.

## Training { #implementation_guide_scale_up_training }


An important step before roll up, is the training of the users and if necessary, the training of the teams providing support to the users. There are many training strategies that you can follow and it will depend on the size of the group that needs to be trained, their skill level, the time frame available, the budget, etc. It is important that you put time and energy into designing your training strategy and allocate enough time to accomplish your training goals. Having your users well trained and informed will reduce user’s anxiety and adoption problems and it will also increase the quality of the data collected.

### Technical Preparations for the Training { #implementation_guide_scale_up_techinical_prep }


When preparing for the training, ensure that all the practical technical requirements have been met. This includes having the tablets/mobile devices ready, with the new DHIS 2 Capture Android Application installed. Depending on the availability of internet connectivity at the area where you will be performing the training, you might have all the tablets pre-synched with the server, so that you have enough data and the right configuration for the training.. Before doing the training, the exercises should be tested to ensure everything is working. Troubleshoot issues detected during testing so they do not arise during training. You may want to do a second round of the test to spot any issues missed in the first round.

If the training is done with pre-synched data and configuration, at the end of the training, make sure to let the trainees experience the App accessing the DHIS 2 remote server. This will give the trainees the possibility to experience real-life sync experience, which may include delays in the network. Without experiencing delays, they may later interpret network delays as faults in their device.

### Training Budget { #implementation_guide_scale_up_budget }


Following, there are some guidelines on preparing the budget which are taken from the [DHIS 2 Community Health Information System Guidelines](https://s3-eu-west-1.amazonaws.com/content.dhis2.org/Publications/CHIS+Guidelines+En.pdf) published by the University of Oslo:

- Follow organizational policies in using approved budget templates and rates (indirect, DSAs, etc.) for all expenses including:
  - Travel (e.g. fuel, car hire, lodging)
  - Personnel (e.g. per diems, meal costs)
  - Venue (e.g. conference space, tea breaks)
  - Materials (e.g. printing, hardware, projectors)
  - Miscellaneous items
- Build budget based on in-sheet calculations of materials needed, unit cost of that material, and number of units needed. You can also build in additional multipliers to illustrate number of units per attendee. This allows flexibility in updating the budget if unit costs change, or number of participants increases or decreases.
- Budget anticipated expenses in local currency, with a conversion rate built in (that can be updated as needed) to convert to the desired currency of your organization or funder.(2).

### Training Agenda { #implementation_guide_scale_up_agenda }


The [DHIS 2 Community Health Information System Guidelines](https://s3-eu-west-1.amazonaws.com/content.dhis2.org/Publications/CHIS+Guidelines+En.pdf) document written by the University of Oslo recommends that you consider:

1. The type of seating you require (round table, individual desks, etc.).
2. Technological requirements (computers for all, Wi-Fi bandwidth, etc.),
3. Finance for conference center allowances, participant food and beverages
4. Trainers need space to walk around to observe and help each participant.

Be aware of the number of attendees you expect at each training, as providing sufficient materials and space will be necessary. Event space should be large enough for the group and also appropriate for the planned activities.

### Training Materials { #implementation_guide_scale_up_materials }


In the same document we find recommendation for the training materials as well, which we include here. The materials you will need for your trainings will depend on your activities. To ensure you are planning for everything, walk through your training agenda with a partner, and discuss what will be done for each part of the training, taking note of the materials needed.

The agenda for training sessions should be defined well-ahead of the training and included in materials distributed.

User documentation should be packaged in Minimal Manuals. These manuals explain a specific work task (e.g. enter monthly data from village health register or compare health in your village with the neighboring villages). After explaining the work task, the Minimal Manual provides numbered step-by-step instructions with screenshots, so that users recognize what to do. Keep in mind that Minimal Manuals do NOT explain the functionality of the app, one by one, like a typical vendor user manual. Since users prefer doing and not reading, the manuals should be a short as possible while still containing all steps.