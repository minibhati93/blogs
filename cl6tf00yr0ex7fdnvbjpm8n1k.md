## How to configure Jest for unit testing in an Angular application

Today, we will learn how to configure Jest in an Angular application. Angular application by default comes with Karma/Jasmine for unit testing so we need to follow some steps to configure Jest in our applications.

## What is Jest?
[Jest](https://jestjs.io/) is a popular test framework for JavaScript.

## Why Jest?

Let's understand first *Why should we even bother to use Jest?*

- It is really fast.
- Executes test from the terminal. No need for the browser to run.
- Offers inbuilt *codeCoverage*

## Uninstall Karma & Jasmine
Before installing Jest, uninstall Karma and Jasmine from your project
```
npm uninstall karma karma-chrome-launcher karma-coverage-istanbul-reporter karma-jasmine karma-jasmine-html-reporter

``` 

## Install Jest
```
npm install jest @types/jest jest-preset-angular --save-dev
```

## Set up Jest in the project

- Remove **karma.conf.js** and **src/test.ts**
- Create a `setupJest.ts` file in the root and import `'jest-preset-angular/setup-jest';` inside of it.

## Configuration at the end of package.json
Add the following configuration at the end of the `package.json` file
```
  "jest": {
    "preset": "jest-preset-angular",
    "setupFilesAfterEnv": [
      "<rootDir>/setupJest.ts"
    ],
    "testPathIgnorePatterns": [
      "<rootDir>/node_modules/",
      "<rootDir>/dist/"
    ],
    "globals": {
      "ts-jest": {
        "tsconfig": "<rootDir>/tsconfig.spec.json",
        "stringifyContentPathRegex": "\\.html$"
      }
    }
  }
```

## Modify tsconfig.spec.json
Add `jest` in the compiler options
```
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/spec",
    "types": [
      "jest",
      "node"
    ]
  },
  "files": [
    "src/polyfills.ts"
  ],
  "include": [
    "src/**/*.spec.ts",
    "src/**/*.d.ts"
  ]
}
``` 

## Remove test block from angular.json
```
"test": {
          "builder": "@angular-devkit/build-angular:karma",
          "options": {
            "main": "src/test.ts",
            "polyfills": "src/polyfills.ts",
            "tsConfig": "tsconfig.spec.json",
            "karmaConfig": "karma.conf.js",
            "inlineStyleLanguage": "scss",
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "src/styles.scss"
            ],
            "scripts": []
          }
        },
```

## Warnings
If you encounter the following warning then add `"allowSyntheticDefaultImports": true` in tsconfig.json


```ts-jest[config] (WARN) message TS151001: If you have issues related to imports, you should consider setting `esModuleInterop` to `true` in your TypeScript configuration file (usually `tsconfig.json`). See https://blogs.msdn.microsoft.com/typescript/2018/01/31/announcing-typescript-2-7/#easier-ecmascript-module-interoperability for more information.```


## Finally! Execute the tests
Tests should be successful  in the terminal

![Screenshot 2022-07-28 at 8.17.22 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659019657452/eKIajKDnA.png align="left")

## Github repo for reference
[Angular Jest Demo](https://github.com/minibhati93/angular-jest-demo)

-----
## Thank you for reading! 
If you want have any comments or want to reach out to me, please feel free to follow me on [Twitter](https://twitter.com/devminibhati) or [LinkedIn](https://in.linkedin.com/in/minibhati93?original_referer=https%3A%2F%2Fwww.google.com%2F)
