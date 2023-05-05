# Testing
## Overview
This page explains the testing set up, as well as the basic testing fundamentals used for testing the frontend.

## Frameworks
Here are the two main frameworks used for testing JS code in general as well as React components:
* [Jest](https://jestjs.io) Main testing framework for JS/TS testing
* [Babel](https://babeljs.io) JavaScript compiler to compile Reacts JSX syntax to JavaScript

## Fundamentals
* Run all tests by executing following command in the root directory: ``npm test``
* Test file names shouold follow following structure to be detected by jest: ``<NAME OF COMPONENT TO TEST>.test.<js/ts/jsx/tsx>``
* Test files should be in the same directory as the component under test
* jest configuration file: https://github.com/MathGrass/mathgrass-frontend/blob/develop/jest.config.js
* babel configuration file: https://github.com/MathGrass/mathgrass-frontend/blob/develop/babel.config.json

## Testing with Redux Store
A main aspect of the MathGrass Frontend application is the global redux store, which handles the applications state. There are two ways of testing with the redux store:
* Work with a mocked store using [redux-mock-store](https://github.com/reduxjs/redux-mock-store)
* Work with an instance of the real store
In order to work with the real store some dispatch functions have been added to make testing easier (e.g. resetting the store).

## Examples
So far only unit tests have been implemented. Examples of how to test React components can be seen in the test file for the [assessment component](https://github.com/MathGrass/mathgrass-frontend/blob/develop/src/components/assessment/assessment.test.tsx).
To see an example of how a service is tested have a look at the [websocket service test](https://github.com/MathGrass/mathgrass-frontend/blob/develop/src/websockets/websocketService.test.ts).
