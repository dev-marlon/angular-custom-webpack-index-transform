# Angular Custom Webpack Index Transform

Use this script to choose a custom root template (default is index.html) for building your angular application.

## Requirements
- Angular 9.x
- @angular-builders/custom-webpack@9.x


## Installation

```bash
npm install @angular-builders/custom-webpack@9.2 git+ssh://git@github.com:dev-marlon/angular-custom-webpack-index-transform.git
```

## Usage

### Update the angular build configuration in angular.json

Change builder for build and serve command
```bash
projects.<yourProjectName>.architect.build.builder = "@angular-builders/custom-webpack:browser"
projects.<yourProjectName>.architect.serve.builder = "@angular-builders/custom-webpack:dev-server"

```
Add indexTransform property
```bash
projects.<yourProjectName>.architect.build.builder.options.indexTransform: "node_modules/angular-custom-webpack-index-transform/index.js"        
```

### Add a npm script to package.json

Provide the nodejs process variable `ANGULAR_CUSTOM_WEBPACK_INDEX_TRANSFORM` and assign it with the path to your custom html templates location path before calling the angular cli script.

```bash
scripts.<some-script-name> = "ANGULAR_CUSTOM_WEBPACK_INDEX_TRANSFORM='/src/custom-templates/' ng serve"
```

Everytime you call the npm script, the index transform script will show u a list of available custom templates from the provided path.

## Things to know
- U have to provide the angular assets manually in each of your custom templates
- Changes in the custom template wont bump an automatic rebuild because it cant be watched by the serve command right now.
