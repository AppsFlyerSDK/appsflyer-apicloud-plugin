



<img src="https://www.appsflyer.com/wp-content/uploads/2016/11/logo-1.svg"  width="200">

# APICloud
The APICloud Library for AppsFlyer SDK

[![npm version](https://badge.fury.io/js/react-native-appsflyer.svg)](https://badge.fury.io/js/react-native-appsflyer)

----------
In order for us to provide optimal support, we would kindly ask you to submit any issues to support@appsflyer.com

*When submitting an issue please specify your AppsFlyer sign-up (account) email, your app ID, production steps, logs, code snippets and any additional relevant information.*

----------


## Table of content

- [Supported Platforms](#this-plugin-is-built-for)
- [Installation](#installation)
    - [iOS](#installation_ios)
    - [Android](#installation_android)
- [API Methods](#api-methods)
    - [initSdk](#initSdk)
   
- [Demo](#demo)


## <a id="this-plugin-is-built-for"> This plugin is built for

- iOS AppsFlyerSDK
- Android AppsFlyerSDK

## <a id="installation"> Installation

`$ npm install react-native-appsflyer --save`


### <a id="installation_android"> Android

##### **android/app/build.gradle**


Run `react-native link react-native-appsflyer` from of the project root or add manually:

Add the project to your dependencies
```gradle
dependencies {
...
compile project(':react-native-appsflyer')
}
```

##### **android/settings.gradle**

Add the project

```gradle
include ':react-native-appsflyer'
project(':react-native-appsflyer').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-appsflyer/android')
```

If you need to override sdk version, add custom configuration to your root gradle, for example:

```gradle
ext {
    minSdkVersion = 16
    targetSdkVersion = 25
    compileSdkVersion = 25
    buildToolsVersion = '25.0.3'
}
```



Build project so you should get following dependency (see an Image):

![enter image description here](https://s26.postimg.org/4ie559jeh/Screen_Shot_2016_11_07_at_5_02_00_PM.png)

##### **MainApplication.java**
Add:


1. `import com.appsflyer.reactnative.RNAppsFlyerPackage;`

2.  In the `getPackages()` method register the module:
`new RNAppsFlyerPackage(MainApplication.this)`

So `getPackages()` should look like:

```java
    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
            new MainReactPackage(),
            //...
            new RNAppsFlyerPackage(MainApplication.this)
            //...
      );
    }
```



## <a id="api-methods">  API Methods

---

Call module by adding:

`import appsFlyer from 'react-native-appsflyer';`

---


##### <a id="initSdk">  **`appsFlyer.initSdk(options, callback): void`**

initializes the SDK.

| parameter   | type                        | description  |
| ----------- |-----------------------------|--------------|
| `options`   | `Object`                    |   SDK configuration           |


**`options`**

| name       | type    | default | description            |
| -----------|---------|---------|------------------------|
| `devKey`   |`string` |         |   [Appsflyer Dev key](https://support.appsflyer.com/hc/en-us/articles/207032126-AppsFlyer-SDK-Integration-Android)    |
| `appId`    |`string` |        | [Apple Application ID](https://support.appsflyer.com/hc/en-us/articles/207032066-AppsFlyer-SDK-Integration-iOS) (for iOS only) |
| `isDebug`  |`boolean`| `false` | debug mode (optional)|

*Example:*

```javascript
const options = {
devKey: "<AF_DEV_KEY>",
isDebug: true
};

if (Platform.OS === 'ios') {
options.appId = "123456789";
}

appsFlyer.initSdk(options,
(result) => {
console.log(result);
},
(error) => {
console.error(error);
}
)
```

---

## Demo

This plugin has a `demo` project bundled with it. To give it a try , clone this repo and from root a.e. `react-native-appsflyer` execute the following:

```sh
npm run setup
```
