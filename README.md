# karma-wiredep-away [![Build Status](https://travis-ci.org/Deklin/karma-wiredep-away.svg?branch=master)](https://travis-ci.org/Deklin/karma-wiredep-away)

> Loads npm/yarn dependencies into your test scope. 

If you want to have all of your production or development bower dependencies into your karma tests, such as `sinon` or `jasmine-jquery`, you can easily 
do it with this plugin with the help of `wiredep`


## Simple example

`npm install karma-wiredep-away --save-dev`

Then add into your `karma.conf.js`

```js
module.exports = function(config) {
    config.set({
        frameworks: ['wiredep', 'jasmine'],
        
        //you can configure wiredep from here (optional)
        wiredep: {
            dependencies: true,    // default: true 
            devDependencies: true, // default: false 
            exclude: [ /jquery/, 'bower_components/modernizr/modernizr.js' ],
            overrides: { ... }
        },

        plugins : [ 'karma-wiredep-away' ]
    });
};
```

All the bower dependencies will be included. If some package is missing the `main` section in its `package.json`, you can configure the `overrides` section for that package. 

Also note that plugin should be included in `frameworks` section *before* your test framework
(mocha or jasmine).

