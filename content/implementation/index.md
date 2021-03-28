+++
title = "Implementation"
+++

## Introduction

This page explains the implementation of our system, for reasoning behind the choice of frameworks see our research page.

## Front End

The front end is a [react js](https://reactjs.org/) app using a browser router to simulate the different pages. It also uses [redux js](https://redux.js.org/) for state management.

The `src` folder has four subdirectories worthy of mention:
- `pages`: where the code for all the individual routable pages goes e.g. `/Register` or `/Login`.
- `components`: individual components that may be shared across multiple pages.
- `common`: configuration values and thin wrappers around `api` calls.
- `state`: code that handles state management with redux.

## Deployment

### App & Deploy config

Before the deployment can begin admins need to provide and app config, an example one is given in the root of the repository.

During the deployment the app config is merged with some generated outputs from the deployment to produce a deploy config. Both the front and back ends get a deploy config file automatically generated during a deploy. This file will is in the `.gitignore` file and not be put into the git history. This is because it may contain sensitive or deployment specific information. This is useful for end users but may be cause difficulty with development. This is why for the client side there is `devDeployConfig.json` file so that the developers can provide all team members with a consistent environment. This file is automatically loaded if the front end detects it is running in "development" mode (essentially if the app is run via `npm start` instead of `npm run build`).

### Terraform

The development team can edit the file `terraform/configuration.tf` which describes the state of the deployment and gives Terraform all the information it needs to update the deployment. If we update the app and require new resources Terraform can keep track of the deployed state and update changes in place where possible.

### Deploy script

There is a file called `deploy.py` in the root of the project. The script is designed to be as helpful as possible for people who aren't technically experienced. Before anything begins the script checks for dependencies and common errors such as missing programs or forgetting to login using `az login`. If any of these errors are detected then the program will exit with helpful error messages.

It first runs Terraform and then merges the provided app config to produce the deploy configs. It will then `npm install` all the require packages for both the server and client. For the client it then builds the static react app and uploads it to the server and for the server it just uploads the source files directly.

## Feature Implementation

### SSO Login

Our login system is entirely through Microsoft SSO allowing users to use their university accounts. This has a number of benefits including reducing the need for us to store user account details. We implement this using a redirect flow which we found works better than popups on many devices including mobiles. The system redirects the user to Microsoft's website where the user is prompted to log in. Once they have the user is redirected back to our app along with their access token. We then store this access token is our `redux` state which allows us to query the API on behalf of them. This token is also required by all of our endpoints to verify the identity of the user.

### Two factor Authentication (2FA) and Registration

When users register for lectures they must authenticate that it's actually them using a 2FA code. Before the user can register they must first setup their 2FA. When the user requests to set it up our app calls an Azure function endpoint which generates a new 2FA secret and then stores a record in the database (an Azure Cosmos DB) with the user ID but it marks the record with "has_verified" set to false. This is because the user isn't allow to reset their 2FA (for security as it would defeat the purpose of 2FA) but we don't want to lock it in until the user has verified that they've stored the secret. This is why we ask the user to enter the code once before it's marked as verified. Once this code is entered successfully the user is then able to use the code the register for classes. This is achieved by passing along the registration event to ORCA.

The algorithm for 2FA is TOTP which allows a shared secret to generate 6 digit numbers that are only valid for 30 second periods.

### Settings and Customisation

We store user settings as a JSON string inside an Azure Cosmos DB. Each JSON string is associated with a user ID which uniquely identifies the user. When the user loads a page which is customised by settings the app will call our Azure function endpoint to request the user settings. By default many setting values will be `null`/`undefined`  which is why we automatically fill in these values with a list of defaults. Since it takes some time to download the settings our app for a short amount of time uses these defaults until the real settings can be used.

The Settings page is the only place where users can edit these values. Whenever the user makes a change the system queues an `update` event and as long as the user doesn't edit any more settings within the next 400ms the system will upload the new settings (using an Azure function endpoint). This 400ms period is used to avoid making too frequent updates reducing server costs. The logic is that 400ms is a short amount of time to wait to apply the settings but long enough that if users are typing text into a field we won't generate an unreasonable amount of unnecessary network requests.

The actual application of the settings is dependent on the component that is using them. It may involve change CSS variables, optionally rendering various components and others. The settings system is designed to be very generic so that future improvements can add customisation without server side changes.

### Forms and Well-being page

This page is relatively simple as it only shows some links to forms and their descriptions. The actual content (both the links and descriptions) is entirely generates from the `app_config.yaml` file to allows admins to show whatever they want to the users.

### Information page

On our information page we directly integrate with several APIs including Microsoft Learn, Linkedin Learning and QnA Bot.

The Microsoft Learn and Linkedin Learning tabs both have similar flows which is to allow the user to search for something they need help with and then find direct links to the particular service to allow the user to participate in the course. With Microsoft Learn there is no search API so we have to download the entire catalogue of courses and then search through it locally. We cache the download to avoid extensive network usage. Linkedin Learning provides a search API but for security reasons we don't give access to the tokens that can be used to directly query the API to the client. Instead we provide an Azure function endpoint that acts as a proxy between Linkedin Learning and our app. This proxy also implements automatically refreshing the token whenever it expires.

When our app is deployed the user provides a QnA Bot token which allows us to interact with that API to provide the user with a chat application where they can ask common questions to the bot.