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

