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
projects.<yourProjectName>.architect.build.options.indexTransform: "node_modules/angular-custom-webpack-index-transform/index.js"        
```

### Add a configuration file

Provide the path to the custom templates via a configuration file named `.indextransformrc`

```json
// .indextransformrc
{
  "templatePath": "/path/to/templates/",
  "target": "<target>" // The angular cli build target - optional, default is "serve"
}
```
Everytime you call an angular cli builder script, the index transform script will show u a list of available custom templates from the provided path.

## Things to know
- U have to provide the angular assets manually in each of your custom templates.
- Changes in the custom template won't bump an automatic rebuild because it can't be watched by the serve command right now.
