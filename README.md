# Cordova: Tango Targeting SDK Plugin

Smart engagement with your customers.

For more information please see [our website][1].

## Download
There are three ways you can add *cordova-plugin-tango* to your Cordova project.

#### 1. Add dependency to config.xml
```xml
<plugin name="cordova-plugin-tango" spec="<specify-version>" />
```
#### 2. Add it from npmjs
Navigate to your project and run the following line:

```bash
cordova plugin add cordova-plugin-tango
```

#### 3. Add it from Git
Navigate to your project and run:

```
cordova plugin add https://github.com/tangotargeting/cordova-plugin-tango.git
```

## Installation

- [iOS](https://github.com/tangotargeting/cordova-plugin-tango/blob/master/INSTALLATION-iOS.md)
- [Android](https://github.com/tangotargeting/cordova-plugin-tango/blob/master/INSTALLATION-Android.md)

## Usage

### Find your Tango API Key

The following step requires you to provide the Tango API Key. The easiest way to locate it is to access https://app.tangotargeting.com/integration/android. This is the documentation for integrating Tango with Android. At point 3 you will be able to see the API Key filled in. See the picture below. 

![API Key location](https://raw.githubusercontent.com/tangotargeting/tango-documentation/master/Tango%20SDK%20Api%20Key%20location.png)

**Important:** Make sure you use this key and **NOT** the Public API Key.

### Prepare the SDK

In order to use it correctly, Tango Targeting SDK should be initialized as soon as possible when your Cordova App launches. In your project's ***index.js*** add the following line at the top of your `onDeviceReady` method.

``` 
window.TangoPlugin.initialize('your-tango-api-key');
```

This will register the device on TangoTargeting and prepare it for consuming campaigns.

**Note:** Explicitly initializing Tango is only needed for iOS. On Android the SDK auto-initializez, provided it can find the API Key in the manifest file. See [Android Installation](https://github.com/tangotargeting/cordova-plugin-tango/blob/master/INSTALLATION-Android.md) 

### Trigger an Automated Campaign

Automated campaigns can be triggered using the following method call:

```
window.TangoPlugin.trigger('your-automated-campaign-trigger');
```

You can find `your-automated-campaign-trigger` by clicking on the campaign in your Tango Console.

### Handle custom actions

Handling a custom action is as easy as extending `TangoPlugin` with the following method:

```javascript
window.TangoPlugin.onCustomAction = function(action){
    // identify the action and do stuff
};
```

### Add segments

You can add segments to a device to allow it to widen the pool of campaigns it can receive with the following method:

``` 
window.TangoPlugin.addSegments(["first-segment", "second-segment"]);
```


## Troubleshooting

1. If you completed the integration but don't receive any campaign, make sure you use the the API Key (see above how to find your API Key) and **NOT** the Public API Key.

2. Sometimes, depending on the version of your Cordova Framework version or Cordova wrappers like Ionic or Phonegap, the configurations in **config.xml** may not be applied to the platforms/android/AndroidManifest.xml. To fix this you can use the **cordova-custom-config** plugin which will make sure the configurations will pe applied to their respective platforms.  

## License

```
Copyright 2017 Tango Targeting, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```


[1]: http://tangotargeting.com
