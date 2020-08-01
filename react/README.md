# React best practices
This section contains documentations, best practices, design patterns and hacks with basic code snippets for React

## Project Structure overview
here is the [sample project](./sample-project) structure as tree.

```
sample-project
        ├── app.tsx
        └── src
            ├── adapters
            │   └── index.tsx
            ├── assets
            │   ├── css
            │   │   └── index.tsx
            │   ├── images
            │   │   └── index.tsx
            │   └── index.tsx
            ├── components
            │   └── index.tsx
            ├── config
            │   └── index.tsx
            ├── containers
            │   └── index.tsx
            ├── layouts
            │   └── index.tsx
            ├── redux
            │   ├── actions
            │   │   └── index.tsx
            │   ├── index.tsx
            │   ├── reducers
            │   │   └── index.tsx
            │   ├── store
            │   │   └── index.tsx
            │   └── types
            │       └── index.tsx
            ├── routes
            │   └── index.tsx
            ├── types
            │   ├── enumerations
            │   │   └── index.tsx
            │   ├── index.tsx
            │   └── interfaces
            │       └── index.tsx
            └── utils
                └── index.tsx
```
## Project Structure details

- `src/types`  will have common typescript interfaces/types/enums (should not be confused with reducer-types.
- `src/redux` folder should have /action, /reducers, /store and /types which would contain every stuff related with react-redux. 
- `src/redux/store` Redux application store objects.
- `src/redux/actions` All the Redux actions creators will be under the actions directory. It's highly advised to organize the action creators based on the screens.
- `src/redux/types` Define all the actions types under this directory. Ideally, the organization of this directory should match that of the actions.
- `src/redux/reducers` Holds redux reducers which will utilize redux/actions and redux/types
- `src/adapters` Organize the code by making network and/or async tasks under this directory. (creation of axios instances / all endpoint configuration / axios mock api).
- `src/components` This directory hosts all the dumb React components. They receive props from React components under screens and render themselves and their children accordingly. These components should have no direct association to Redux. Redux actions must instead be passed down from the screens.
- `src/containers` Holds the top level React components. These React components are mounted by the react-router and map the Redux actions and state to props and pass down to the screens. Refrain yourself from having any logic inside these components.
- `src/config` Holds the app specific configuration variables. As always, do not store any secret keys here.
- `src/layouts` All those components which acts as holder/shell should be inside pages or layout folder. 
- `src/routes` All the app routes are defined in this file.
- `src/assets` all the assets for the application should be here. Note : all css should be dash separated style. 
- `src/assets/images` includes images .png .svg .jpg etc
- `src/assets/styles` will have all style related stuffs it includes application themes, css-in-js, less, sass, fonts etc    
- `src/app.tsx` The parent React component of the app. Bridges the react-router and Redux store into the app flow.
 
## Project Structure details

There are no hard rules for these, but maintaining a standard is a must. i read many tech blogs and liked the below ideas.

- Folders and files names should be lower case, and dash separated example `user` or `user-details`
- According to functionality it should be singular or plural example `utilities`, `service-provider`, `store` 
- Every folder should have index file which will act as [aggregation module](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export) 
- If the file is a component, then the extension should be `.tsx` else it has to be `.ts` (only applicable to files inside `/src/*`) 
- Only application level data should be in `store/redux`, every other communication related data should be made via `React.context` api. 
- Try to make as many dumb components as possible (**DRY**: Don’t Repeat Yourself) in a components folder. 
- None of the files in component folder should be connected with application level data like `store/reducer`. This should be plug and play kind of reusable components.


## React Guidelines. 
- Please use `REACT_HOOKS` majorly, as React has declared it the way to code from `16.8.0` version in hooks.
- Please avoid inline styling as much as possible, either create specific styles with css or use **css-in-js** concept.
- Please use specific imports only, as unused imports has problems with build size increments.
- Do not overload render method with **too much business logic**. Try to use react life-cycles/hook providers as much as possible for best performance.

## Routes Guidelines. 
- Handel `404 page` or use default redirection beforehand use React Router Dom version 4 or latest. 
- All routes related logic and rules should be at inside `/src/routes`.

## Test Cases / Mocks Service
- Every test case should be in its respective folder with naming convention `file-name.test.[ts/tsx]`, example `jest/enzyme` testing framework. 
- Use axios mock adapters for core api tests.

## Few very obvious guidelines
- Please separate your `dev dependency` and `main dependency`. 
- Never check-in `node_modules` folder.
- Always have exact versions in `package.json` (remove ^ from ^x.x.x version) **unless you trust the libraries**. 
- Do not install external libraries without trust, make sure that library has good reputation over community example `axios mock`. 

## Editor Guidelines / VSCode hacks
I prefer Visual Studio Code (VSCode) with atom one dark theme.
- Install code spell checker extension. 
- Formatting shortcut (alt+shift+f).

___

## Decision Conflicts
 
**What should we put in environment variables vs config files?**

> All those properties which are different for local/dev/prod environments should be in respective .env files. All the fixed properties such as constants will be in config files. 
 

**How to decide what should be in dependency vs dev-dependency?**
>All those modules which are required to create build should always be in dependency other will be in dev-dependency 
