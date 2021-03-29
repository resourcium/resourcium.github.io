+++
title = "Appendices"
+++

## Introduction

This page contains the user manual, deployment manual and legal issues and processes related to the application we have built.

### User Manual
---
Here is the user manual for the web application (students): [Link to manual](https://drive.google.com/file/d/16ZBPm8gkbL-S01gn4Bn1uSyCVCcG4S6I/view?usp=sharing)

Here is the user manual for lecturers (Sharepoint site): [Link to manual](https://drive.google.com/file/d/14NbWAQz7_IMVK0YVy-QjUTGU-ZaiTsbI/view?usp=sharing)

### Deployment Manual
---

{{ internal_link(path="@/deployment/index.md", label="Link to the deployment manual") }}
\
### A legal statement on source code rights, IP (intellectual property) rights, GRPR of data governance
---
#### Major milestones and Quality Gates

- 1. Implement a login solution so students can use their university credentials to sign in to the web app
- 2. Implement the two factor authentication which represents the front-end system for student class registration
- 3. Setup a Sharepoint site and automate data storage to it via MS Flows where student data is entered via MS Forms
- 4. Setup a section in the web app to allow students to access resources (Linkedin learning and MS Learn APIs)
- 5. Setup the user customisations and settings page
- 6. Create a QnA chatbot and setup a connected Sharepoint list to it
- 7. Integrate the components together as appropriate on the site
- 8. Tidy up the code base and research materials
- 9. Setting up appropriate deployment system

#### Team roles and deadlines
| Major milestones | Responsible Member | Deadline |
| ---------------- | ------------------ | -------- |
| 1                | All                | 20 Dec 2020 |
| 2                | Louis              | 20 Dec 2020 |
| 3                | Hemil              | 15 Jan 2021 |
| 4                | Hemil, Louis       | 30 Jan 2021 |
| 5                | Pritika            | 30 Jan 2021 |
| 6                | Hemil              | 20 Feb 2021 |
| 7                | All                | 10 March 2021 |
| 8                | All                | 24 March 2021 |
| 9                | Hemil, Louis       | 24 March 2021 |

\
#### Potential liabilities
As a group we only have the following liability due to the nature of our project (due to it being open source and deployable by other universities):
\
Our first and only liability is that we need to complete and deliver this project/codebase to our clients by the specified deadline which is
24th March 2021. The final requirements is delivering code that can be deployed onto their own Azure system. Overall the key components would
be the login system, the student registration page, a page for students to access resources which contains a QnA bot as well as a page for student
to fill out forms where this data would be stored in a centralised Sharepoint site. In order to achieve the above features, we have set milestones so our
progress can be supervised and as long as we keep up with the plan, the project should finish on time.

#### Intellectual Property Type
The most appropriate intellectual property type for this project would be the Creative Commons License. This is because the purpose of the CC license is to grant
some or all reserved rights to others. Whereas a trademark is for a identifiable name and a patent is to protect an original idea. The aim of this system is to be a baseline
for other universities to use and extend upon. Our project does not need a identifiable name (though we have called the app UCL Resourcium) as we will not be very famous. Additionally,
a lot of our system is dependent on other 3rd party services and systems, which requires us to learn from them, the work cannot be patented.
\
\
With regards to open source materials and implementations, we have made use of many open source libraries built-in to Node and React. All those libraries are under the open source
license and are free for editing. All images that we have used are either open source or made by us. To use some of the features, a license is required for example Microsoft Flow. The necessary licenses, subscriptions and costs will be detailed in the 'Manufacture Process and Deployment Costing'. Below are the libraries we have used with their respective licenses:
- React library (useState and useEffect) -> Open Source (MIT)
- ReactTwitchEmbedVideo -> Open Source (MIT)
- QRCode -> Open Source (MIT)
- SVG Icons on navigation bar + fontawesome library -> Open Source (MIT)
- MS Bot Framework -> Open Source (MIT)

The source code agreement that is the most logical is open source. Firstly, the aim of the application is to solve student engagement and wellbeing issues within a university environment which is not limited to just UCL. There is no data or packages on the system that prevent it from being shown freely. This means that other universities can download it, use it and distribute it to others. In our case our open source software will be free to be used. An appropriate sub category of open source this would fall under is the MIT license. This type of license is one of the most
permissive licenses available. Copies of the software can be made but a copy of the MIT license and copright notice must be added to it.
\
#### Data privacy and GDPR

The main concern for data privacy is the usage of student data when they login through our system. We use Microsoft Graphs to get some of their basic profile information which we then use to
personalise the application. Additionally we have user settings and preferences also stored in a separate database within Azure.

Firstly, we promote data privacy which means we know we need to keep student data private within the application. Hence, the student will need to provide us with permissions before they log into
our application. In our application, there is no storage of the users details, in fact all of it comes from the API call, and is only used for the session. 

Secondly, we have made sure to use appropriate methods to process data. We have control of where and how the data is processed. The data with regards to the ticketing system is stored in a Sharepoint site which is managed by the university, hence our app does not use this data at all. Additionally, data such as user settings is again stored into the universities Azure account.

Thirdly, we have made sure to use as minimal data as possible to implement this application. For example, in user settings we only store the userID and their colors/schemes/views. In the case
of the ticketing system, our system only stores their email address and the help they require within a university Sharepoint site.

To conclude, our application does not have a data privacy concern as our application does not store data interally. It is all passed onto the university servers (Azure and Sharepoint) to be processed. As long as the university follow the GDPR laws too, there should not be a problem.


#### Manufacture process and deployment costing

Since our system is based off the cloud and many Azure services as well as other subscriptions. Universities will need be a tenant with Microsoft, they will need access to Microsoft 365 including MS Forms, MS Flows Premium, MS Sharepoint. Subscriptions for LinkedinLearning and Microsoft Learn will also be required for it to be usable by the application.
Below is the cost list for each individual part of the app:
- Azure functions:  $0.20 per million executions and $0.000016/GB-s (GB-s is RAM used times seconds executed)
- Cosmos db: $0.008/hour per 100 requests
- MS Flows: £15 per month (per user plan)
- QnABot: First 10,000 messages are free, then every 1000 premium message costs £0.37 (estimated)
- QnAMaker resource: Free option (3 transactions per second) or paid option ($10 per month for unlimited documents)

We cannot estimate the full cost for the client to run the application as we do not know at what scale the application will be used. We would need statistics and data to perform accurate estimates.

### Compliance of ADA and WCAG 2.2

The software also follows the key points of the high compliance systems interfaces:
- The system can be viewed by those with colour deficient vision
- Colour is used redundantly
- Moving text is avoided, or where used it freezes to allow ease of reading
- The sites uses a single, clear legible font
- There is sufficient contrast between text and background colours
- The pages have logical tab orders through all screen elements
- Each page has a descriptive title
- The system avoids blinking and flickering
- The system uses common web conventions
- The system uses pop-up windows appropriately
\

### Application End-User License Agreement (EULA)
---

With no contract provided from UCL (our client), we drafted this EULA to protect our intellectual property as well as our client's.

#### End-User License Agreement ("Agreement")
Last updated: March 13, 2020

Please read this End-User License Agreement carefully before using the UCL Resourcium Application.

#### Interpretation and Definitions
---
##### Interpretation

The words of which the initial letter is capitalized have meanings defined
under the following conditions.

The following definitions shall have the same meaning regardless of whether
they appear in singular or in plural.

##### Definitions

For the purposes of this End-User License Agreement:

* Agreement means this End-User License Agreement that forms the entire
agreement between You and the Company regarding the use of the
Application.
* Application means the software web application provided by Hemil Shah, Pritika Shah
and Louis De Wardt available via a website.
* Hemil Shah, Pritika Shah & Louis De Wardt (referred to as either "the Company", "We",
"Us" or "Our" in this Agreement) refers to UCL Resourcium Web app.
* Content refers to content such as text, images, or other information that
can be posted, uploaded, linked to or otherwise made available by You,
regardless of the form of that content.
* Country refers to: United Kingdom
* Device means any device that can access the web Application such as a
computer, a cellphone or a digital tablet.
* Third-Party Services means any services or content (including data,
information, applications and other products services) provided by a
third-party that may be displayed, included or made available by the
Application.
* You means the individual accessing or using the web Application or the
company, or other legal entity on behalf of which such individual is
accessing or using the Application, as applicable.

#### Acknowledgement
---

By using the web Application, You are agreeing to be bound by the terms and conditions of this Agreement. If You
do not agree to the terms of this Agreement do not use the Application.

This Agreement is a legal document between You and the Company and it governs
your use of the Application made available to You by the Company.

#### License
---

##### Scope of License

The Company grants You a revocable, non-exclusive, non-transferable, limited
license use the Application strictly in accordance
with the terms of this Agreement.

The license that is granted to You by the Company is solely for your personal,
non-commercial purposes strictly in accordance with the terms of this
Agreement.

##### License Restrictions

You agree not to, and You will not permit others to:

* Remove, alter or obscure any proprietary notice (including any notice of
copyright or trademark) of the Company or its affiliates, partners,
suppliers or the licensors of the Application.

#### Third-Party Services
---

The Application may display, include or make available third-party content
(including data, information, applications and other products services) or
provide links to third-party websites or services.

You acknowledge and agree that the Company shall not be responsible for any
Third-party Services, including their accuracy, completeness, timeliness,
validity, copyright compliance, legality, decency, quality or any other aspect
thereof. The Company does not assume and shall not have any liability or
responsibility to You or any other person or entity for any Third-party
Services.

You must comply with applicable Third parties' Terms of agreement when using
the Application. Third-party Services and links thereto are provided solely as
a convenience to You and You access and use them entirely at your own risk and
subject to such third parties' Terms and conditions.

#### Term and Termination
---

This Agreement shall remain in effect until terminated by You or the Company.

The Company may, in its sole discretion, at any time and for any or no reason,
suspend or terminate this Agreement with or without prior notice.

This Agreement will terminate immediately, without prior notice from the
Company, in the event that you fail to comply with any provision of this
Agreement.

Upon termination of this Agreement, You shall cease all use of the Application.

Termination of this Agreement will not limit any of the Company's rights or
remedies at law or in equity in case of breach by You (during the term of this
Agreement) of any of your obligations under the present Agreement.

#### Indemnification
---

You agree to indemnify and hold the Company and its parents, subsidiaries,
affiliates, officers, employees, agents, partners and licensors (if any)
harmless from any claim or demand, including reasonable attorneys' fees, due
to or arising out of your: (a) use of the Application; (b) violation of this
Agreement or any law or regulation; or (c) violation of any right of a third
party.

#### No Warranties
---

The Application is provided to You "AS IS" and "AS AVAILABLE" and with all
faults and defects without warranty of any kind. To the maximum extent
permitted under applicable law, the Company, on its own behalf and on behalf
of its affiliates and its and their respective licensors and service
providers, expressly disclaims all warranties, whether express, implied,
statutory or otherwise, with respect to the Application, including all implied
warranties of merchantability, fitness for a particular purpose, title and
non-infringement, and warranties that may arise out of course of dealing,
course of performance, usage or trade practice. Without limitation to the
foregoing, the Company provides no warranty or undertaking, and makes no
representation of any kind that the Application will meet your requirements,
achieve any intended results, be compatible or work with any other software,
applications, systems or services, operate without interruption, meet any
performance or reliability standards or be error free or that any errors or
defects can or will be corrected.

Without limiting the foregoing, neither the Company nor any of the company's
provider makes any representation or warranty of any kind, express or implied:
(i) as to the operation or availability of the Application, or the
information, content, and materials or products included thereon; (ii) that
the Application will be uninterrupted or error-free; (iii) as to the accuracy,
reliability, or currency of any information or content provided through the
Application; or (iv) that the Application, its servers, the content, or
e-mails sent from or on behalf of the Company are free of viruses, scripts,
trojan horses, worms, malware, timebombs or other harmful components.

Some jurisdictions do not allow the exclusion of certain types of warranties
or limitations on applicable statutory rights of a consumer, so some or all of
the above exclusions and limitations may not apply to You. But in such a case
the exclusions and limitations set forth in this section 11 shall be applied
to the greatest extent enforceable under applicable law. To the extent any
warranty exists under law that cannot be disclaimed, the Company shall be
solely responsible for such warranty.

#### Limitation of Liability
---

Notwithstanding any damages that You might incur, the entire liability of the
Company and any of its suppliers under any provision of this Agreement and
your exclusive remedy for all of the foregoing shall be limited to the amount
actually paid by You for the Application or through the Application.

To the maximum extent permitted by applicable law, in no event shall the
Company or its suppliers be liable for any special, incidental, indirect, or
consequential damages whatsoever (including, but not limited to, damages for
loss of profits, loss of data or other information, for business interruption,
for personal injury, loss of privacy arising out of or in any way related to
the use of or inability to use the Application, third-party software and/or
third-party hardware used with the Application, or otherwise in connection
with any provision of this Agreement), even if the Company or any supplier has
been advised of the possibility of such damages and even if the remedy fails
of its essential purpose.

Some states/jurisdictions do not allow the exclusion or limitation of
incidental or consequential damages, so the above limitation or exclusion may
not apply to You.

#### Severability and Waiver
---

##### Severability

If any provision of this Agreement is held to be unenforceable or invalid,
such provision will be changed and interpreted to accomplish the objectives of
such provision to the greatest extent possible under applicable law and the
remaining provisions will continue in full force and effect.

##### Waiver

Except as provided herein, the failure to exercise a right or to require
performance of an obligation under this Agreement shall not effect a party's
ability to exercise such right or require such performance at any time
thereafter nor shall be the waiver of a breach constitute a waiver of any
subsequent breach.

#### Product Claims
---

The Company does not make any warranties concerning the Application. To the
extent You have any claim arising from or relating to your use of the
Application, the Company is responsible for addressing any such claims, which
may include, but not limited to: (i) any product liability claims; (ii) any
claim that the Application fails to conform to any applicable legal or
regulatory requirement; and (iii) any claim arising under consumer protection,
or similar legislation.

#### Changes to this Agreement
---

The Company reserves the right, at its sole discretion, to modify or replace
this Agreement at any time. If a revision is material we will provide at least
30 days' notice prior to any new terms taking effect. What constitutes a
material change will be determined at the sole discretion of the Company.

By continuing to access or use the Application after any revisions become
effective, You agree to be bound by the revised terms. If You do not agree to
the new terms, You are no longer authorized to use the Application.

#### Governing Law
---

The laws of the Country, excluding its conflicts of law rules, shall govern
this Agreement and your use of the Application. Your use of the Application
may also be subject to other local, state, national, or international laws.

#### Entire Agreement
---

The Agreement constitutes the entire agreement between You and the Company
regarding your use of the Application and supersedes all prior and
contemporaneous written or oral agreements between You and the Company.

You may be subject to additional terms and conditions that apply when You use
or purchase other Company's services, which the Company will provide to You at
the time of such use or purchase.

#### Contact Us
---

If you have any questions about this Agreement, You can contact Us:

* By email: hemil.shah.19@ucl.ac.uk | louis.dewardt.19@ucl.ac.uk | pritika.shah.19@ucl.ac.uk


