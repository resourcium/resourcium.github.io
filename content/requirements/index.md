+++
title = "Requirements"
+++

## Intro to Project Background and Clients
Currently, students do not have any simple ways of conveying their wants and needs to staff members at 
universities. Additionally, staff have no easy way of collecting data and categorising them in order to see
what students really enjoy about their lectures. Our client was UCL, a world-renowned university in the heart of
London. They currently have an exisiting system that provides data based on submissions on a system known as Moodle
but it lacks suitable measures for student feedback and engagement.
## Project Goals
Our project goal is to increase student engagement with staff members and allow staff at UCL to easily monitor how their students
are doing in relation to their courses. In technical terms, our project is oriented around developing a responsive web
application that serves students and stores data about what they need in terms of resources for staff to see. The application should also
provide appropriate help to students in terms of resources. 

### Client Requirements
An online meeting was arranged via Microsoft Teams with our clients.
During the meeting, we received our list of requirements which consisted of things that must be implemented and some extras which
can be implemented depending on our timeframe. Initially, multiple meetings were conducted in order to produce a clear MoSCoW and remove
any ambiguities. Below are example questions that we asked the clients:

- What type of application are we developing (desktop or mobile)?
- Is there any example applications that already exist?
- Is there a particular endpoint or server this application should work with? (Sharepoint e.g.)

## Personas

![Jon Brown's Persona](./Persona1.png)
![Eva Smith's Persona](./Persona2.png)

## Scenarios

### Jon Brown

Jon is a CS student who is currently in 2nd year. He has a strong interest in quantum computing. He knows that his university has research currently ongoing in that area and he is unaware of whom to contact. He decided to use our web application to get further insight in this matter. He found it easy to navigate through the web application which contained a search form to ask him what topic area he is looking for. He found the hierarchical system informative and easy to understand. Using the same system he was able to find which staff member to approach to fix his license key issues. Every week he is further prompted by the system to give feedback on his current lectures, so the course can be improved towards his liking (i.e. help increase his course satisfaction).

### Eva Smith
Eva Smith is a CS lecturer who is currently researching quantum computing. She knows that students are somewhat engaged via the use of an online system called Moodle. She wants to know which students are regularly attending their online lectures and she does not want to waste time with a conventional register during the online lecture. Therefore, she uses our web application to give a code to everyone who is attending, which would be then used by the students to confirm their attendance via our web application. Additionally, she wants feedback on how well she is performing in her lectures. The system contacts students via a chatbot weekly to get feedback. The system generates a word cloud using sentiment analysis and presents it to the lecturer. 

## Use Case list:
The purpose of a use case list is to identify exactly who is going to the use the website, what the user wants to do and how the website should respond to actions. Below
is what we have identifed as necessary for the users:

### University Students:

- a. User can login to the web app via SSO (university login details)
- b. User can navigate to any page they want to on the app
- c. User can fill out appropriate forms from the Wellbeing Section in the app
- d. User can switch between different RESTful APIs on the homepage (switch from Twitch Stream to Twitter Page)
- e. User can go into settings and change colors or background images as well as their preferences
- f. User can register for their timetabled lecture
- g. User can access a tree-diagram of staff and pHD students in the university (Deprecated case)

### University Staff Members:

Initially we were planning to build a front-end system for the staff as well according to our sketches. However, later meetings with the clients suggested that
they wanted data stored within Sharepoint to be seen via a Sharepoint dashboard instead. Below is the use-case list for staff via an expected Sharepoint system:

a. Staff can see student responses to a form
b. Staff can see the data presented via some visualisation (maintained by the staff themselves)
c. Staff can monitor a students attendance for the whole year (This task has been removed because another team ORCA is developing the backend for this (an entry
point for our application)).

## MoSCoW Requirements List

### Must Haves:

- There must be a login page for students to use their existing university details to login by
- Data must not be stored about students on anywhere but the organisations' Sharepoint system
- There must be a 2 factor authentication system to validate students when they register for classes which we must design ourself
- Students can report their stress levels and workloads as well as pain points anonymously within their course.
- An admin dashboard on Sharepoint to view this data.
- The app must be generic enough to work for other universities (any specific scopes/data requirements will need to be defined)

### Should Haves:

- There should be a way to allow students to access extra resources for their course or whatever they may be interested in
- The app should be customisable by students (for example changing color schemes) where settings will be stored in a database
- The system should feature a ticketing system where staff members and course representatives respond to the additional help required by the student in their course and an 
automated email should be sent to the student regarding their query as acknowledgement

### Could Haves:
- The system could have a page dedicated to helping students further their careers via a shared calendar that they can access to see upcoming events
- The system could feature things that are currently happening at the university, via blogs, social medias etc. (this will require scripting and web scraping)
- The system could allow additional features to be added, essentially a architecture that is extensible.
- The system would like to have a QnA bot that can assist students in help they need.
- If a QnA bot is implemented then the bot must be easily extendable (staff should be able to update the QnA database via a Sharepoint list)

### Would Haves:
- None

### Things we won't have:
- The backend for the registration of students as this would require a strong coupling between the app and a particular function/API provided by the university. In this case, universities will have to design their own backend for registration to a lecture and connect it to our front end two factor authentication where we can specify the point of connection.


### Non-functional requirements:
- The application must be responsive (Must)
- The application must be deployable by other universities (Must)
- The source code should be open source and freely available (Should)
- The application should have a reasonable response time when users search for resources (Should)

Note: Requirements may change over the course of the year according to the clients' demand.