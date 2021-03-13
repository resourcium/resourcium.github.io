+++
title = "Evaluation"
+++

## Introduction

This page explains the summary of achievements, critical evaluation of the project and future work.

### Summary of achievements
---
#### Achievement Table for MoSCoW list

#### List of known bugs

There is currently no known bugs, which we have identified during testing of the application. Our team used github issue tracker in order to keep track of bugs that we may have encountered
during testing or implementation stages. This helped to keep the bug list empty.

#### Individual contribution table

### Critical evaluation of project
---
In this section we will critically evaluate our project with respect to the following factors:
- User interface: We have used a common system of having a navigation bar to go through the different pages. We also ensured that simplicity and readability were kept as the top target for the web application. Generally, the UI is easy to use as described by our testers. They are happy with how easily accessible everything is on the web application. We have put in a lot of work to make the system clean and user friendly. However, the only downside to the UI would be its desktop version. Responsive testing for different screen sizes suggests that even though the UI is readable and usable, it does not look as visually appealing. This is documented as part of the future work. For more information on the testing, head over to the testing section.
\
\
Overall, we can mark ourselves "good" for the UI work.
\
\
\
- Functionality: Since we have achieved all the key functionalities and 40% of the optional functionalities, the app can be seen as providing a lot functionality. We have made sure to use a generic system design so other universities can deploy scripts to setup the web application for their own use. Students can view twitter, twitch, find links within their university, look for resources on Linkedin Learning, look for resources within MS Learn, communicate with a QnA bot for queries, report their stress levels, get additional help on their studies or modules and change their preferences from the settings page. Most importantly students can also register for their lectures (this applies to our UCL client only for which a backend is being developed by the ORCA team).
\
\
Overall, we give ourselves "very good" for functionality completion
\
\
\
- Stability: Our team has done a lot of testing and achieved a good test coverage. We also have continuous integration setup within our github repository which is a formatter and linter ensuring the code written is to a good quality and standard. With these measures and a high test coverage, we can say the application is stable.
\
\
Overall, we give ourselves "good" for the stability section.
\
\
\
- Efficiency: 


### Future Work
---

If we had more time the following things is what would be appropriate to look into:
1. The first thing that should be done is that there should be a redesign of the user interface for the desktop version of the site. Even though the website scales well into a desktop version,
it deviates from how a standard desktop site looks. However, the user interface looks good on tablet and mobile devices.
2. A native version of the web application should be made. Since the app already exists as a React application, it would be appropriate to make a corresponding mobile application in React Native. This will probably improve the experience of the user as well.
3. Currently, there is no easy/simple way of automating deployment to a Sharepoint site (currently our system requires some manual deployment from the client via the videos we have made). If in the future there is a way of automating this deployment from Microsoft, this should be applied to our system. 
4. The architecture of the web application can be redesigned so that it is extensible, currently the system does allow extensibility but requires modification of a fair number of parts of the application. So a redesign of the base of the system to instead use "extends" from a single App component to add more components would make the system significantly neater.
5. Considering universities want to learn on student stresses and wellbeing, data collected from the application can be mined via machine learning in terms of their wants and needs. Our system currently just stores this data and displays it.