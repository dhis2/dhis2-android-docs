# Data Security and Privacy { #implementation_guide_datasec }

With the new DHIS 2 Android Capture App, users will be collecting individual data at the point of service provision, which is the lowest level of direct data capture as it involves the direct beneficiary. Capturing Data this way enables upstream analytics without compromising on detail, makes downstream analytics possible, reduces error and enables post hoc analysis to answer questions identified after data collection and system design. However, individual data brings additional challenges for information systems, including considerations of security and privacy, considerations of readiness and capacity, as lower IT literacy data collectors are provided with digital tools and additional complications with regards to analytics, storage and system responsiveness.

There is wide consensus on the need to provide a comprehensive data security practice. This comprehensive security practice should consideot only *confidentiality* and *integrity,* but also *availability of data*. Harvard Humanitarian Initiative has [stated](https://hhi.harvard.edu/publications/signal-code-ethical-obligations-humanitarian-information-activities) that information itself, including its generation, communication and reception, is a basic humanitarian need that should be afforded protection equal to other such traditional needs as food, water, shelter, and medical care. The Roadmap for Health Measurement anccountability (MA4Health), [stated](https://www.healthdatacollaborative.org/fileadmin/uploads/hdc/Documents/the-roadmap-for-health-measurement-and-accountability.pdf) that “Public health and clinical care cannot be delivered safely, with high quality, and in a cost-effective manner, without seamless, sustainable and secure data and information exchanges at all levels on the health system”. Still, the capture and storage of personally identifiable data introduces risk and a commensurate obligation for rigorous privacy practices.

The University of Oslo is committed to the following:

1. Ensuring that the DHIS 2 software development and release process is subject to a transparent and rigorous security verification plan;
2. Through an action research approach, the university seeks to learn by doing in solidarity with others; 
3. Striving to develop, learn and share relevant, timely and useful information and tools to promote good security practice;
4. Access to any and all health information in the course of our practice will be governed by strict and mutual agreement;
5. Using the university's actions to provide good example of security practice.

There can be a tension between the health system’s need for identifiable data, and the patient’s right to privacy. In the absence of clear legislation governing the collection and storage of personally identifiable data, there are important concepts that should be understood and promoted by system owners and implementers. They include:

**Right of access**

: The right of access will be defined by the data protection regulations of each country. In general terms, it includes information about the processing purposes, the categories of personal data processed, the recipients or categories of recipients, duration of storage, information about the rights of the data subject such as rectification, erasure or restriction of processing, the right to object, information about the existence of an automated decision-taking process, including profiling, etc.  Please be aware of the regulations specific to your area and make sure you are ready to comply before you start collecting data.

**Right of erasure**

: The right of erasure is also defined by the data protection regulations of each country. In general terms, personal data must be erased immediately where the data are no longer needed for their original processing purpose, or if the data subject has withdrawn his/her consent and there is no other legal ground for processing. Again please make sure you understand the regulations of your specific area and make sure you are ready to comply.

**Data minimization**

: The basic idea of data minimization is that data processing should only use as much data as is required to accomplish a given task. It also implies that data collected for one purpose cannot be used for another purpose other than original processing one without further consent.

**Pseudonymization**

: It is a data management procedure that makes personal data less identifiable while keeping it suitable for analysis and processing. It can be accomplished by replacing the value of some of the data fields by one or more artificial identifiers, or pseudonyms. Pseudonymized data can be restored to make individuals identifiable again, while anonymized data can never be restored to its original state. Depending on the regulations applicable to your area, you can define a Pseudonymization strategy that meets the regulations and meets your needs.

**Traceability**

: In order to use data effectively we need to ensure its integrity. In order to ensure its integrity, it is important to monitor these data when they are collected, processed and moved. You need to understand: “what”, “when”, “why” and “who”. Organizations that take advantage of traceability, are able to find data faster and are better able to support security and privacy requirements.

Based on the regulations of your territory and the complexity of your project, including the level of potential risk, you must implement appropriate technical and organisational measures, such as pseudonymisation, data minimisation, audit logs, search restrictions, granular sharing, etc, and integrate the necessary safeguards into the data processing in order to meet the requirements of the regulations that apply to your region.

An adequate security / privacy approach for any DHIS2 implementation capturing personally identifiable data would include the creation of a clear policy naming an individual(s) with full access to the system, with the responsibility to ensure the following. For any technical support on databases containing sensitive data, a signed NDA with a clear end-date should be required for any third parties. 

|   | Possible practical implementation |
| --- | -------------------------------------------------------------------------- |
| **Right of access &  Right of erasure** | Giving access to the patient to his / her record electronically for its review or deletion is not available in DHIS 2 (2.32). You should ensure that you put in place other methods by which a patient can request a copy of his/ her record so he/ she can review it and request amendments or its deletion. If its deletion is not possible, you should anonymize the record by removing / replacing all identifiable data points. |
| **Data minimization** | Ensure that there is a valid reason for collecting personal identifiable data. Don’t collect unnecessary details which don’t serve a practical purpose in terms of data analysis or the need of finability of a patient record. For example, if the need for patient follow-up gets determined by a test result being positive, don’t collect patient name if the result is negative.|
| **Pseudonymization** | Consider using alternative values for recording information about certain procedures or conditions of a patient. Por example you can have a list of medical procedures / personal behavior / actions listed as a color list. This allows to do analytics, without revealing what could be a stigmatized procedure/ action/ behavior in a given territory. |
| **Traceability** | DHIS 2 provides detailed audit log for each data point. This includes the tracing of data captured via its web tools (from 2.22), as well as imported or via Android (from version 2.27). Currently (2.32) DHIS 2 does not provide a full deletion / anonymization export option, as deletion of a value preserves previous data in the audit log. For this reason, any sharing of exported data to outside parties should include manual removal of sensitive / identifiable data. |

## Practical Security Considerations for Android Implementations { #implementation_guide_dhis2_config_sec }


### Using DHIS 2 sharing restrictions { #implementation_guide_dhis2_config_sec_sharing }


In this section we will share some tips on how to use DHIS 2 sharing and share restrictions to ensure that only the right users have access to records with identifiable information.

Here is a practical example of granular sharing and search restrictions in the context of a Health Care Center for Maternal and Newborn Care:

Midwife User Role:

- Can search across three programs across all org units in the district
- Can enroll new pregnant women into ANC program
- Can add/edit events to clinical assessment program stage
- Can view all ANC data in own org unit

Lab tech User Role

- Can search across one program org units in the district
- Can add/edit events to lab program stage
- Cannot view clinical assessment stage

MOH Supervisor User Role

- Can view dashboard only

It is very important to have standard operating procedures (SOPs) as part of your Data Protection Strategy.

A SOP is a set of step-by-step instructions compiled by your organization to help you carry out complex routine operations such as those related to data security.

SOPs helps your organization achieving efficiency, quality and consistency, while complying with Data Protection regulations.

When defining your Data Protection SOPs you should address questions such as:

- What is the relevant existing legislation?
- Who is the named controller? Processor? Data Protection Officer?
- Who is tasked with reviewing audit logs?
- What is your process for removing old users?
- Bring your own device?
- Hardware security?
- Mutual Confidentiality Agreements

We include here some SOP Best Practices taken from the [DHIS 2 Community Health Information System Guidelines](https://s3-eu-west-1.amazonaws.com/content.dhis2.org/Publications/CHIS+Guidelines+En.pdf) document published by the University of Oslo:

1. Harmonize multiple programs into a single data capture protocol.
2. Develop SOPs for each individual community project especially if multiple data flows exist.
3. Turn the SOP into illustrated posters and have the facility staff post them on their walls for public viewing.
4. Print SOPs and make sure all CHWs, facility staff, and district staff have copies
5. Stakeholders to sign the SOPs at the completion of training.
6. Stakeholder participation in the creation and approval of SOPs. The SOPs must institutionalize the best practices and workflow of the actors in the CHIS. Include representation from all relevant stakeholders in the process of developing SOPs.
7. Ensure all data elements and indicators are captured. The CHWs should clearly understand the meaning, and measurement of each data element and indicator to remove ambiguity
8. Use data capture guidelines at trainings. To build accountability, CHWs and facility staff need to know they are part of a larger system. They need to know how their data is used for planning at higher levels and specific actions at lower levels.
9. Have the CHWs explain the data capture guidelines. This teach-back method is an effective adult learning practice. By explaining the data capture guidelines, this elevates the CHW’s credibility with the health committee.
10. Produce, simple-to-use, local language guidelines. CHWs and facility staff need guides and instructions on what to do. Consider making posters or small laminated portable data capture guidelines for CHWs and facilities to put on the wall or carry with them that outline their role and responsibilities based upon the data capture guidelines.
11. Have CHWs, facility, district staff and national staff sign guidelines. This is a symbolic “commitment” measure. The aim is that they have read it, understand their reporting responsibilities as defined in the data capture guidelines, and will carry out these responsibilities.
12. Produce simple videos or audio and upload them to phones. Responsibilities and actions for every event are made easier with a simple, local-language videos or audio guides that facility staff and CHWs can refer to.


### Practical Data Security Guidelines { #implementation_guide_dhis2_config_sec_practical }


Ensuring that the personal data stored on mobile devices is only accessible by the authorized health staff starts by educating users on how to use this data and ensure that it is kept secured at all times. The guidelines below are an extract taken from the PSI’s “Monitoring and Evaluation Standard Operating Procedures for Keeping Client Data Secure & Confidential” manual.

![](resources/images/implementation-guide-image31.png){ .center }

System administrators play an important role when configuring user’s access-level, by ensuring that their data access is appropriate and never unnecessarily excessive. The guidelines below are also part of PSI’s “Keeping Client Data Secure & Confidential Administrators Guide” manual

.![](resources/images/implementation-guide-image13.png){ .center }