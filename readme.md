# Power BI visual using external libraries

This is an example of how to use external libraries in Power BI custom visuals. This visual uses JQuery and lodash installed from NPM.

![Power BI visual using JQuery and lodash](screenshot.png)

#### Version Notice
This visual is built using v1.2.0 of the custom visual API. As of v1.2.0 visuals loaded in Power BI are not provided lodash or jQuery by default. This means that if you want to use these libraries you have to include them in your visual which means you do not need to worry about Power BI changing the version of JQuery or lodash and potentially breaking your visual AND it means you can include whatever version you'd like.

#### Running this visual

It is generally considered a best practice to not check-in npm modules or typings. Instead the `package.json` and `typings.json` include a list of the dependencies of the project and you need to install them before you can run the project.

To download / run this visual follow these steps:

* download or clone this repo
* Open terminal / command line in the root of the project
* run `npm install` - this will install modules listed in `package.json`
* run `typings install` - this will install type definitions listed in `typings.json`
* run `pbiviz package` - this will create a pbiviz in the `dist` directory
* load the generated pbiviz into PowerBI

#### Useful links

* [NPM](https://www.npmjs.com/)
* [Typings](https://github.com/typings/typings)
* [Power BI Visuals Tools (pbiviz)](https://github.com/microsoft/powerbi-visuals-tools)
* [Power BI Visuals Documentation](https://github.com/microsoft/powerbi-visuals)
 
## Step by Step Instructions

You an use any libraries you'd like in custom visuals by following these steps. Additionally, you can look at the commit history of this repository to see the actual file changes starting from the base visual (generated using the pbiviz command line tools).

### Install libraries from npm

You can install any js modules you'd like to use by simply running `npm install`.

Be sure to use the `--save` flag to add these dependencies to your package.json file.

**Example - install jquery and lodash via npm**

```bash
npm install --save jquery lodash
```

### Load libraries into visual

Once you have your js library (via npm or just by manually downloading a js file) simply add a reference to the file in your `tsconfig.json`

**Example tsconfig.json - reference jquery and lodash installed via npm**

```json
"files": [
    ...
    "node_modules/jquery/dist/jquery.js",
    "node_modules/lodash/lodash.js",
    ...
]  
```

### Install type definitions using typings

You can add type definitions (d.ts files) manually or by using typings. 

**Example - install jquery and lodash type definitions**

```bash
typings install --save --global dt~lodash dt~jquery
```

### Referencing typings type definitions in your visual

Once you've installed your first d.ts from typings you'll need to reference the `index.d.ts` file in the typings directory in your `tsconfig.json`.

Note: this only needs to be done once. All future type definitions installed via typings will be added to the index.d.ts file automatically.

**Example tsconfig.json - reference typings d.ts entry point**

```json
"files": [
    ...
    "typings/index.d.ts",
    ...
]  
```
