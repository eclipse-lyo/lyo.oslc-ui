# OSLC UI

[![](https://img.shields.io/badge/project-Eclipse%20Lyo-blue?color=418eeb)](https://github.com/eclipse/lyo)
[![Discourse users](https://img.shields.io/discourse/users?color=28bd84&server=https%3A%2F%2Fforum.open-services.net%2F)](https://forum.open-services.net/)


- [How to use](#how-to-use)
  - [oslc-selector](#oslc-selector)
  - [oslc-preview](#oslc-preview)
- [Development](#development)
  - [Dev server](#dev-server)
  - [Code scaffolding](#code-scaffolding)
  - [Build](#build)
  - [Running unit tests](#running-unit-tests)
  - [Running end-to-end tests](#running-end-to-end-tests)
- [Further help](#further-help)

## How to use

1. After cloning this git repository, go the root folder of the repo.
2. run `npm run build:elements-prod` to build the project. This will produce a `dist` with artefacts
3. Copy the `dist` folder to under `/src/main/webapp/static/` of your web project. That is, you will have a number of js/css files under the folder `/src/main/webapp/static/dist/oslc-ui`
4. Add the following dependency to your Java app:

```
<dependency>
    <groupId>org.eclipse.lyo.server</groupId>
    <artifactId>oslc-ui-model</artifactId>
    <version>4.1.0-SNAPSHOT</version>
</dependency>
```

### oslc-selector

Add the following code to your html page:

```html
<oslc-selector
  no-data-text="No data..."
  search-placeholder-text="Type here..."
  selection-uri=""
  fields=""
></oslc-selector>
```

Usage example in a page:

```html
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html;charset=utf-8">
        <link rel="stylesheet" href="<c:url value="/static/dist/oslc-ui/styles.css"/>">
    </head>
    <body>
        <oslc-selector selection-uri="<%= selectionUri %>" fields='["oslc:label"]'></oslc-selector>

        <script src="<c:url value="/static/dist/oslc-ui/runtime-es2015.js"/>" type="module"></script>
        <script src="<c:url value="/static/dist/oslc-ui/runtime-es5.js"/>" nomodule defer></script>
        <script src="<c:url value="/static/dist/oslc-ui/polyfills-es5.js"/>" nomodule defer></script>
        <script src="<c:url value="/static/dist/oslc-ui/polyfills-es2015.js"/>" type="module"></script>
        <script src="<c:url value="/static/dist/oslc-ui/main-es2015.js"/>" type="module"></script>
        <script src="<c:url value="/static/dist/oslc-ui/main-es5.js"/>" nomodule defer></script>
    </body>
</html>
```

- Note that `<%= selectionUri %>` is jsp-code that points to the Selection DelegatedUI. You can use any other logic to define this URI.
- Note also that `fields='["oslc:label"]'` can be any list of values from the json result returned.

The selected items can then be retrieved using the [OSLC 3.0 Delegated Dialogs](https://docs.oasis-open-projects.org/oslc-op/core/v3.0/ps01/dialogs.html#client_responsibilities) API.


### oslc-preview

`<oslc-preview input-data=""></oslc-preview>`

## Development

### Dev server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

### Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

### Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

### Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

### Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 9.0.5.
