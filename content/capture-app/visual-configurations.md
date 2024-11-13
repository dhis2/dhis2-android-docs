# Visual configurations { #capture_app_visual }

##  Local Analytics (Improved 3.0)

### Data Visualizations { #capture_app_visual_data_visualizations }

The DHIS2 Android App can now render analytics that have been created in the Data Visualizer app in DHIS2. Analytics to be displayed require to be configured using the Android Settings WebApp where administrators will be able to decide the charts and tables to be displayed for end users.

To configure analytics open the Android Settings WebApp on your DHIS2 server and follow the steps below:

   1. Select Home, Program or Data set from the Analytics menu
   2. Select the visualization type "Data visualization"
   3. Click on the  "Add Visualization" button
   4. Search by typing the name of the visualization and select it by clicking on it
   5. Add an alternative title, otherwise, the app will display the name of the visualization

![](resources/images/capture-app-image162.png){ width=25%}
![](resources/images/capture-app-image164.png){ width=25%}

Analytics are created and configured using the web tools, however, the data aggregation happens offline using only data stored in the device.  

![](resources/images/capture-app-image165.png){ width=25%}
![](resources/images/capture-app-image166.png){ width=25%}
![](resources/images/capture-app-image167.png){ width=25%}

#### Analytics Types and Filters

The analytics supported in the Android App are:

   - Pivot Tables
   - Column Chart
   - Line Chart
   - Pie Chart
   - Radar chart
   - Single Value

For each visualization object, the user will be able to filter in the app by:

   * Relative Period: Daily, Weekly, Monthly, Yearly, This Quarter, Last Quarter, Last 4 Quarters and Quarter this year.
   * OrgUnit: Select "All" to display all the org units available to the user or "Selection" to specify one or multiple org units.

![](resources/images/capture-app-image180.png){ width=25%}
![](resources/images/capture-app-image168.png){ width=25%}
![](resources/images/capture-app-image169.png){ width=25%}

A reset button will be displayed if a filter is applied. Select Reset to display the default visualization.

![](resources/images/capture-app-image170.png){ width=25%}

Users can also change The anlytics type between chart, table or single value.

![](resources/images/capture-app-image166.png){ width=25%}
![](resources/images/capture-app-image171.png){ width=25%}

#### Legends { #capture_app_visual_data_visualizations_legends }

Legends are displayed in pivot tables by enabling the feature "Use legends for chart color" in the Data Visualizer App.

The Android app will color the cells using either the pre-defined legend per data item or a single legend for the entire pivot table, depending on the settings in Web.

The style for legends in tables has a new design which ensures good contrast and visibility independently from the selected colour for the legend.

![](resources/images/capture-app-image183.png){ width=25%}

#### Groups { #capture_app_visual_data_visualizations_groups }

All these visualizations can be organised and displayed in groups. Groups are also configured using the Android Settings Webapp following the steps below:

   1. Open the Android Settings App
   2. Click to Add a new visualization in the Analytics Menu (Home, Program or Data set)
   3. Select a visualization
   4. Mark the "Use a group visualization" checkbox
   5. Create or select a created group
   6. Save the visualization

You can name your different groups, they will be displayed as a button in the top bar of the analytics screen.

![](resources/images/capture-app-image173.png){ width=25%}

#### Limitations { #capture_app_visual_data_visualizations_limitations }

Android uses tables and charts created using the web Visualizer app, however only the configuration parameters of the object are used by the Android App: data elements, indicators, chart type, title, periods...; all the aggregations are calculated offline by the android application. The results will be based on the data stored in the device at that exact moment.

Since the aggregations and calculations displayed are calculated in the device, the implementation of analytics is limited compared to web. In summary the compatible and suported objects and features are:

   - Well formed analytic objects (series, categories, filters)
   - Use of relative periods (Fix periods are not supported)
   - User has view access
   - Limitations for Pivot Tables
      - Number of header lines: 1 or 2 (from 2.3)
      - Number of header columns: 2
   - Limitations for Charts
      - Number of Series: No limit (but remember you are rendering in a small screen)
      - Number of Categories (doesn’t apply for pie chart): No limit

There are many more restrictions which apply to Android Analytics regarding the many configuration options available in the Web Visualizer as well as the supported functions and calculations related to indicators and program indicators. [This table](https://docs.google.com/spreadsheets/d/1127cz7M0K4fux5CU0V54V2Z77NZWCr0BTrZ6jcCec4Q) summarises all supported features.

> **Note**
>
> The following aggreagation functions are supported now in local analytics: LAST, FIRST, AVERAGE_SUM_ORG_UNIT, LAST_AVERAGE_ORG_UNIT, LAST_IN_PERIOD, LAST_IN_PERIOD_AVERAGE_ORG_UNIT, FIRST_AVERAGE_ORG_UNIT
> 
> 

### Event Visualizations (New 3.0) { #capture_app_visual_event_visualizations }

The DHIS2 Android App can now render analytics that have been created in the line listing app.Analytics to be displayed require to be configured using the Android Settings WebApp where administrators will be able to decide the tables to be displayed for end users.

To configure analytics open the Android Settings WebApp on your DHIS2 server and follow the steps below:

   1. Select Home or Program from the Analytics menu
   2. Select the visualization type "Event visualization"
   3. Click on the  "Add Visualization" button
   4. Search by typing the name of the visualization and select it by clicking on it
   5. Add an alternative title, otherwise, the app will display the name of the visualization 
    
In the app, the users will be able to search by period, Org. unit, or any of the columns added in the Line List.

![](resources/images/capture-app-image265.png){ width=25%}
![](resources/images/capture-app-image266.png){ width=25%}
![](resources/images/capture-app-image267.png){ width=25%}

#### Limitations { #capture_app_visual_event_visualizations_limitations }

To add an event visualization in the Android Settings WebApp, the table must:

- be created in the Line Listing app
- use relative periods
- not exceed 15 columns

## Interface language

The language of the interface will corespond to the language set in the DHIS2 user configuration. If the language is not available in the app, it will pick the language of the device. 

If none of the language configurations are available, the app will default to English.

Translations set up in DHIS2 for metadata will also be shown according to the language in the user configuration.

![](resources/images/capture-app-image182.png){ width=25%}


## Personalize your Icon { #capture_app_visual_icon }

You can set your icon in the wallpaper using the DHIS 2 App Widget. The icon will be the flag configured in your server.

![](resources/images/capture-app-image32.jpg){ width=25%}

> **Note**
>
> How to add a widget:
>
> - Long press in your wallpaper
> - Select Widgets
> - Look for the DHIS 2 Widget
> - Select
>
> It will add a shortcut to your app.

## Personalise the colour of the App { #capture_app_visual_colour }

You can set the generic theme of the app by configuring the them in our server:

![](resources/images/capture-app-image28.png){width=80% }

> **Note**
>
> How to set the server theme and flag:
>
> Go to **System Settings > Appearance > Style**
>
> - Select your style
>   - Green,
>   - India (Orange),
>   - Light Blue,
>   - Myanmar (red),
>   - Vietnam
> - Select your flag
>
>![](resources/images/capture-app-image23.png){ width=25%}

## Icon library for metadata (Improved 3.0) { #capture_app_visual_icon_lib }

There are currently 134 icons available that you can choose from. You can search by name in the icon picker widget. Icons are available in positive, negative and outlined shapes.

Icons can be associated to programs, stages, data elements and the options of an option set. This is  configurable through the Maintenance App.

> **Note**
>
> This feature is available from DHIS 2 2.30 onwards

![](resources/images/capture-app-image13.png){ .center width=80% }

In the DHIS2 Android App icons render in the home screen to illustrate all the programs available to a user, or while adding an stage. For data elements and options, the icons render for single event programs, when a section contains a single or more DEs, showing the option set as a matrix or sequence of images.

The icon based data entry can now be used in enrollment forms. When an enrollment section contains one or more Tracked Entity Attributes with option sets and icons assigned, the app is able to display them as a matrix or sequence based on the section rendering type. In previous sections of the App this feature was only available for Data elements.

![](resources/images/capture-app-image19.png){ width=25%}
![](resources/images/capture-app-image26.png){ width=25%}

From 3.0 it is possible to display custom icons in the Android App. DHIS2 (41 version) now allows uploading custom Icons to be used in addition to the built-in Icon library. This is useful for use cases not related to health or that require very specific iconography. The Android App will render the custom icons that need to be uploaded and configured using the Maintenance DHIS2 Web App.

To upload and assign the custome icons through the instance, the admin must:

1. Open the object (program, data element, option, etc.)
2. Click on the "Select icon"
3. Click on the "Choose file to upload"
4. Add a key and description
5. Save

![](resources/images/capture-app-image290.png){ width=25%}

> **Note**
>
> Icons will initially only render in the new Android app. The new web-based Capture App will incorporate them in the near future.

We plan to expand the collection of icons on each future version of DHIS2 for that we need your help: we are seeking ideas for new icons - please submit yours using [this form](https://www.google.com/url?q=https://drive.google.com/open?id%3D1LmfYJQAu3KyDfkY3X6ne7qSsuTa9jXZhoQHzkDxeCdg&sa=D&ust=1557433016147000).

## Colour palette for metadata { #capture_app_visual_colour_palette }


Tracker and Event capture now have the ability to render colours for programs, stages, data elements and options in option sets. A colour picker is integrated in the Maintenance App, which shows as a palette, except for options which allows the selection of any colour.

![](resources/images/capture-app-image20.png){ .center width=80% }

In the Android App, the color will be rendered as background color for programs and stages combined with an icon (if selected). For options it renders as the background colour during data entry form for single event programs. When the user selects a program with an assigned colour, that colour becomes the background theme for all screens in the domain of the program.

![](resources/images/capture-app-image19.png){ width=25%}
![](resources/images/capture-app-image2.jpg){ width=25%}

> **Note**
>
> Colours will first be available in the new Android app, followed in future releases by the new web-based Capture App.

## Rendering Types for Program Sections { #capture_app_visual_rendering_type }


![](resources/images/capture-app-image16.png){width=80% }

**Program Section**: when used in combination with icons, a Program Section with one or more data elements and associated Option Sets can render the options in sequential or matrix layout (see screenshots). If the icon is not found, the app displays the DHIS logo.

![](resources/images/capture-app-image26.png){ width=25%}
![](resources/images/capture-app-image36.png){ width=25%}

From 2.8, the app will render option set with any value type as matrix or sequential layout.

![](resources/images/capture-app-image226.png){ width=25%}
![](resources/images/capture-app-image227.png){ width=25%}

> **Note**
>
> Render type for sections will first be available in the Android app, followed in future releases by the new web-based Capture App UI.

## Calendar { #capture_app_visual_calendar }


Now it is possible to use two different calendars. The one on the left is the first to appear but you can change it by clicking on the calendar icon on the lower left corner.

This is available when:

1. Making a new enrollment.
2. Creating a new event (Programs with and without registration).
3. Using period filters in data sets and programs with and without registration.

![](resources/images/capture-app-image60.jpg){ width=25%}
![](resources/images/capture-app-image61.jpg){ width=25%}

> **Note**
> 
> For Android versions 4.4,  5.1 and small devices, the Accept option is not visible in the second calendar view.

## Render types { #capture_app_visual_render }

The available rendering options have been expanded to include horizontal and vertical radio buttons, checkboxes and toggles for any value type.

![](resources/images/capture-app-image111.png){ width=100%}
![](resources/images/capture-app-image224.png){ width=25%}
![](resources/images/capture-app-image225.png){ width=25%}

> **Note** 
>
> The default rendering option will automatically display a search box whenever there are more than 15 elements in the option set to ease the selection.
> 
> ![](resources/images/options_no_search.png){ width=25% } ![](resources/images/options_search.png){ width=60% }

Render types are available in event and registration forms

### QR and Barcodes { #capture_app_visual_render_qr }


Data elements or attributes type text can be also configured as QR or barcodes. When a Data Element or Attribute is rendered as QR/Barcode, the app will open the device camera to read the code image. When the QR/Barcode is a TEI attribute configured as searchable, the user will be allowed to scan the code in order to search and identify the Tracked Entity Instance. This will also work for option sets.

Barcodes also allow the user to manually enter the value.

![](resources/images/capture-app-image118.png){ width=20%}
![](resources/images/capture-app-image119.png){ width=20%}
![](resources/images/capture-app-image120.png){ width=20%}
![](resources/images/capture-app-image121.png){ width=20%}


#### Export/Share

Users are now able to display a bar or QR code in an image so that it can be shared for printing, take a screenshot or show it on the screen for scanning.

Non-editable fields can still share the bar or QR code, but will prevent the user from capturing a new one.

![](resources/images/capture-app-image181.png){ width=20%}
![](resources/images/capture-app-image174.png){ width=20%}

#### GS1 Data Matrix codes { #capture_app_visual_gs1 }

If an attribute or data element rendering type is configured as QR code, the Android App will be able to read and process the string as GS1 Data Matrix codes.

Combined with the use of d2 functions in program rules, the different fields of a GS1 code can be saved into different data elements or attributes (d2:extractDataMatrixValue(key, dataMatrixText)).

![](resources/images/capture-app-image184.png){ width=20%}
![](resources/images/capture-app-image200.png){ width=20%}

### Signature (Improved 3.0) { #capture_app_visual_signature }

This feature allows users to collect handwritten signatures from the device. The signatures will be saved as an image data element in the app.

This configuration must be done in web ( available from 2.40 version) by selecting the "canvas" rendering type on an image value type.

![](resources/images/capture-app-image231.png){ width=20%}
![](resources/images/capture-app-image232.png){ width=20%}

From 3.0, signatures are allowed to be opened in full screen for better visibility.

## User Experience { #capture_app_visual_user_experience }

### Tappable areas in icons and buttons { #capture_app_visual_tappable_areas }

Some buttons or tappable labels of the Android App had small sensitive areas for the user to tap. The whole user interface was reviewed and the tappable areas has been increased. For example the "+" button to create a new stage or the "˅" icon to open TEI details or expand a section.

![](resources/images/capture-app-image208.png){ width=20%}

### Loading Banners { #capture_app_visual_loading_banners}

The Android App provides visual animations to users when they perform actions that take longer than usual to complete, such loading maps or searching, so that they know that the system is processing their request.

![](resources/images/capture-app-image228.png){ width=20%}

### Offline Buttons { #capture_app_visual_offline_buttons}

This feature enhances the functionality of the app when it is used offline, ensuring that menus are disabled when the online actions are not available.

### Long Texts Management { #capture_app_visual_longtext_management}

The Android App enables users to view long text in fields that are limited in size, such as a stage names or datasets headers.

### Legends (Improved 3.0) { #capture_app_visual_legends_descriptions}

The Android App displays the full description of the legend when tapping on the information icon once a legend is active. These feature is available only in event and registration forms.

![](resources/images/capture-app-image276.png){ width=25%}
![](resources/images/capture-app-image277.png){ width=25%}

### Input fields (Improved 3.0) { #capture_app_visual_input_fields }

The new input fields are now displayed by default in the Android app and admin users are able to opt-out to use the old forms through the Android Settings web app.

![](resources/images/capture-app-image289.png){ width=25%}

### New menus update (Improved 3.1.0) { #capture_app_visual_menu_update}

The new