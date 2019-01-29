# Existing Data Solutions at SDU

## OneDrive:

OneDrive is a storage platform at SDU  provided by MicroSoft that can store small to medium amounts of live data (typically word or excel documents, photos, videos, etc).
OneDrive can be used to store and share sensitive and confidential data. OneDrive supports local file synchronization à la DropBox, although with many limitations on filenames.
OneDrive supports sharing of individual files/folders with other users. It is possible to grant limited and full access to files (WS3/80, WS3/86).
OneDrive can store sensitive data and detailed logging and access control is implemented (WS3/42). OneDrive has the ability to let the user attach metadata by an API on individual files and make it searchable (WS2:2/3). However such metadata support (e.g. what files refer to whom for sensitive data) is not implemented at SDU in any automatic way. Therefore procedures have been established for the users to follow, in case they store sensitive data for long periods of time (>30 days) on OneDrive.
Since OneDrive can synchronize data to local (and insecure) drives, care should be taken for synchronization of sensitive data.  

- WS3/80: Allow for collaboration on analysis platform
- WS3/86: Allow for external collaboration on data analysis
- WS2:2/3: Metadata describing owner and affiliation
- WS3/42: Enforce strict access policies to data. Maintain detailed log of all operations and access to data

## NextCloud:

NextCloud is storage platform is use at SDU, similar in functionality to OneDrive described above. The solution is based on the open-source NextCloud v13 software. 
As OneDrive, it can store can store  small to medium amounts of live data.
NextCloud supports sharing of individual files/folders with other users. It is possible to grant limited and full access to files (WS3/80, WS3/86).
Support for sensitive data is also similar to OneDrive. NextCloud can store sensitive data detailed logging and access control is implemented (WS3/42). NextDrive has the ability to add "tags" to data, which could be used as a limited form of metadata.

- WS3/80: Allow for collaboration on analysis platform
- WS3/86: Allow for external collaboration on data analysis
- WS2:2/3: Metadata describing owner and affiliation
- WS3/42: Enforce strict access policies to data. Maintain detailed log of all operations and access to data

## Secure Server  (“Sikker Server”)

This a pure terminal server / remote desktop solution that is used for execution of softwares like “Stata” or "Spss" in a controlled environment. It offers limited computational support with a range of standard analysis tools.
Sensitive data can be processed within the environment as long as they are pseudo anonymized.

??

# SDU Cloud - new data solution at SDU

SDUCloud platform is a new solution in development at SDU for research data.
We have implemented a number of features based on the work in this activity.
SDUCloud is a service for live research data, which provides secure data storage, data analysis/processing, and discoverability of data. Such integrated solutions are sometimes called "Virtual Research Environments".

??

## Storage

The storage platform of SDUCloud is designed to store all kinds of live research data.
This includes large datasets, as well as sensitive or confidential data. 
The storage support provided by SDUCloud is similar in functionality to the many other "cloud storage" solutions, e.g. OneDrive, Google Drive and, Dropbox. We provide a "virtual drive" for both research projects (shared folders) and personal accounts (private documents).

Keeping sensitive data requires to perform strict access control and
detailed logging. For this we implemented a system-wide audit of all operations in the system (WS3/42). The system also supports encryption at rest and in transit.

- WS3/42: Enforce strict access policies to data. Maintain detailed log of all operations and access to data

All research projects in the system have associated structured metadata. This
includes the project's data management plan. A structured data management
plan allows us to standardize certain parts of it. We can, for example,
automatically destroy/preserve data at the end of a project (WS2:2/2), or perform scheduled backups.

- WS2:2/2: Data must be preserved according to an agreement

As research is commonly a collaborative discipline, the platform supports
sharing of individual files/folders with other users. It is possible to grant
limited or full access to files (WS3/80, WS3/86).

- WS3/80: Allow for collaboration on analysis platform
- WS3/86: Allow for external collaboration on data analysis

The SDUCloud platform aims to make data discoverable. 
We have implemented support in the system for attaching metadata to individual files and make it searchable (WS2:2/3). We are also planning to further implement domain specific metadata (WS3/30, WS2:2/6).

- WS2:2/3: Metadata describing owner and affiliation
- WS3/30: The metadata that provides the traceability back to the biobank sample that was analyzed must be preserved through the analysis pipeline.
- WS2:2/6: Metadata targeted at the designated community

## Compute

SDUCloud ships with a "store" of applications. An SDUCloud application is a tool created to facilitate analysis of data and runs in the "cloud"
(WS3/17). The app store acts as a directory of tools (WS3/71). Tools can be tagged and searched for. 
Each tool contains a concrete and machine readable description of the tool. This
metadata includes, among others, software versions, fields, and references to
documentation (WS2:2/11, WS3/35, WS3/39).

- WS3/17: Computers for analysis
- WS3/71: Keep directory of tools for analysis
- WS2:2/11: Metadata describing versions of software in the pipeline and its TRL.
- WS3/35: Exact versions of used software must be documented
- WS3/39: Version controlled workflows / machine readable workflows in open format

During the design of the SDUCloud compute platform we had a large focus on
reproducibility, automation, and traceability. We implemented reproducibility
by using Docker for managing the software stack inside of applications.
Docker allows to create a "container" of software in the exact versions needed (WS3/31, WS3/41, WS3/40, WS3/82). These containers are portable and can easily move between different hardware.

- WS3/31: It must be possible to keep the same software stack for a whole study
- WS3/41: Software versioning and validation
- WS3/40: It must be possible to recreate the desired software stack on demand
- WS3/82: Keep versions of software and data sync'ed for team members, if needed

When an application is executed, the platform saves job results and job parameters
to a system folder in the user virtual drive. This step archives both the results
and input parameters, allowing to re-run the application at a later point in
time (WS3/76).

- WS3/76: Easy archiving ('freeze') of analysis

We plan to extend the platform to allow the composition of individual applications together to create a workflow. We define workflows using machine readable documents, like the ones used for applications (WS2:2/9, WS2:2/10, WS3/65).

- WS2:2/9: Validated and documented process and software
- WS2:2/10: Declaration of pipeline for data processing
- WS3/65: Record steps in the workflow: success, error, restarts


# Requirements

I couldn't find a stable persistent identifier for each requirement. I used
the following format: `WS<number>[:<tab>]/<row>`

- WS3/10: Standardization, controlled open data (FAIR), AI for quality control & analysis
- WS3/17: Computers for analysis
- WS3/30: The metadata that provides the traceability back to the biobank sample that was analyzed must be preserved through the analysis pipeline.
- WS3/31: It must be possible to keep the same software stack for a whole study
- WS3/35: Exact versions of used software must be documented
- WS3/39: Version controlled workflows / machine readable workflows in open format
- WS3/40: It must be possible to recreate the desired software stack on demand
- WS3/41: Software versioning and validation
- WS3/42: Enforce strict access policies to data. Maintain detailed log of all operations and access to data
- WS3/47: Reuse workflows
- WS3/65: Record steps in the workflow: success, error, restarts
- WS3/71: Keep directory of tools for analysis
- WS3/76: Easy archiving ('freeze') of analysis
- WS3/80: Allow for collaboration on analysis platform
- WS3/82: Keep versions of software and data sync'ed for team members, if needed
- WS3/86: Allow for external collaboration on data analysis
- WS2:2/3: Metadata describing owner and affiliation
- WS2:2/2: Continuously available data collection
- WS2:2/2: Data must be preserved according to an agreement
- WS2:2/6: Metadata targeted at the designated community
- WS2:2/9: Validated and documented process and software
- WS2:2/10: Declaration of pipeline for data processing
- WS2:2/11: Metadata describing versions of software in the pipeline and its TRL.
