# Cordova: Tango Targeting Plugin

Smart engagement with your customers.

For more information please see [our website][1].

## Installation (Android)

### Add the SDK Key
Tango Targeting SDK auto-initializez on Android. However, it needs to read your Tango SDK Key from AndroidManifest.xml file. In your `config.xml` add the SDK Key to the android platform in the following manner:

```xml
<platform name="android">
  <!-- other configurations above -->
  <config-file parent="./application" target="AndroidManifest.xml">
    <meta-data android:name="tango_api_key" android:value="your-tango-sdk-key" />
  </config-file>
  <!-- other configurations below -->
</platform>
```

### Enable Tango logs

If you want to see Tango logs add a `tango_debug_mode` `meta-data` set to `true` to your android platform.

```xml
<meta-data android:name="tango_debug_mode" android:value="true" />
```

### Enable Push Notifications

Tango Targeting uses FCM for push notifications. For this you will need a [Firebase](https://firebase.google.com/) account. After successfully creating the account follow this steps.

1. Go to [Firebase Console](https://console.firebase.google.com/);
2. Add a new project;
3. When the project is created, click on *Add Firebase to your Android app*. A popup window will open with 3 steps;
4. In the first step your android package name is required. This can be found in your project's *config.xml* file. Look for `<widget android-packageName="com.yourapp.android" />` if `android-packageName` is missing, use the `id` attribute;
5. Click **Register app**. It will take you to step 2;
6. Download the file *google-services.json* and copy it in the root folder of your cordova project;
7. Close the pop-up window;
8. Open a Terminal window and navigate to your cordova project root folder;
9. Run `cordova build android`;

To finalize the process, copy the FCM **Server key** and **Sender Id** from here:
![FCM Server Key and Sender Id location](https://github.com/tangotargeting/tango-documentation/blob/master/fcm-server-key-location.png?raw=true)

Then go to *Tango Console -> Apps* and add them to your app.

![Tango Server Key and Sender Id location](https://github.com/tangotargeting/tango-documentation/blob/master/tango-server-key-location.png?raw=true)

Hit the **Update** button.

**Note:** If you don't see your app yet, click **New app** to add it. Use the same package name you used for FCM.

### Permissions

