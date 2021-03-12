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

### Deploy config

Both the front and back ends get a deploy config file automatically generated during a deploy. This file will is in the `.gitignore` file and not be put into the git history. This is because it may contain sensitive or deployment specific information. This is useful for end users but may be cause difficulty with development. This is why for the client side there is `devDeployConfig.json` file so that the developers can provide all team members with a consistent environment. This file is automatically loaded if the front end detects it is running in "development" mode (essentially if the app is run via `npm start` instead of `npm run build`).

