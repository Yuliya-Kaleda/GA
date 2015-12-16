### Designing for multiple devices

Android devices come in many shapes and sizes all around the world. With a wide range of device types, you have an opportunity to reach 
a huge audience with your app. In order to be as successful as possible on Android, your app needs to adapt to various device 
configurations. Some of the important variations that you should consider include different languages, screen sizes, and versions of the
Android platform.

#### Supporting Different Languages

It’s always a good practice to extract UI strings from your app code and keep them in an external file. Android makes this easy with 
a resources directory in each Android project. To add support for more languages, create additional values directories inside res/ that 
include a hyphen and the ISO language code at the end of the directory name. For example, values-es/ is the directory containing simple 
resources for the Locales with the language code "es". Android loads the appropriate resources according to the locale settings of the 
device at run time. The folder structure will look like this:

![](https://cloud.githubusercontent.com/assets/10750398/11850638/b00e7ef2-a43f-11e5-97d8-2edc99aca02e.png)

Add the string values for each locale into the appropriate file. At runtime, the Android system uses the appropriate set of string resources based on the locale currently set for the user's device. For example, the following are some different string resource files for different languages.

English (default locale), /values/strings.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="program">General Assembly</string>
</resources>
```

Spanish, /values-es/strings.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="program">Asamblea General</string>
</resources>
```
It is a good practice to reference your string resources in your source code and other XML files using the resource name defined by the ```<string>``` element's name attribute.

##### Example:

* Reference in code:
```
    TextView textView = (TextView) findViewById(R.id.view);
    textView.setText(R.string.program);
```
* Reference in xml file:

```
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/program" />
```

#### Supporting Different Screens

Android categorizes device screens using two general properties: 
* size: small, normal, large, xlarge
* density: low (ldpi), medium (mdpi), high (hdpi), extra high (xhdpi), extra extra high (xxhdpi)
 
To declare different layouts and bitmaps you'd like to use for different screens, you must place these alternative resources in separate directories, similar to how you do for different language strings.

###### Create Different Layouts
To optimize user experience on different screen sizes, you should create a unique layout XML file for each screen size you want to support. Each layout should be saved into the appropriate resources directory, named with a ```-<screen_size>``` suffix. For example:

![](https://cloud.githubusercontent.com/assets/10750398/11787480/e1db3fac-a259-11e5-9874-de95420af6a3.png)

 This project includes a default layout and an alternative layout for large screens. The file names must be exactly the same, but their contents are different in order to provide an optimized UI for the corresponding screen size.
 Also be aware that the screens orientation (landscape or portrait) is considered a variation of screen size, so many apps should revise the layout to optimize the user experience in each orientation. By default, the layout xml files are used for portrait orientation. To reference a lanscape orientation, the folder should add the suffix -land: 
 
 ![](https://cloud.githubusercontent.com/assets/10750398/11794335/cd4f40f4-a27e-11e5-8fa4-2ea7a2f81316.png)
 
###### Create Different Bitmaps
 
All bitmap resources should be properly scaled to each of the generalized density buckets: low, medium, high and extra-high density. To generate images, you should start with your raw resource in vector format and generate the images for each density using the following size scale:

- xhdpi: 2.0
- hdpi: 1.5
- mdpi: 1.0 (baseline)
- ldpi: 0.75

After the images are ready, they are placed in the appropriate drawable resource directory. For example:

![](https://cloud.githubusercontent.com/assets/10750398/11794684/98b1926e-a280-11e5-8dbf-6750034c1b0a.png)
 
Any time you reference ```@drawable/android.png```, the system selects the appropriate bitmap based on the screen's density.

#### Supporting Different API Levels

API Level is an integer value that uniquely identifies the framework API revision offered by a version of the Android platform. The API Level identifier serves a key role in ensuring the best possible experience for users and application developers:

* It lets the Android platform describe the maximum framework API revision that it supports
* It lets applications describe the framework API revision that they require
* It lets the system negotiate the installation of applications on the user's device, such that version-incompatible applications are not installed.

While the latest versions of Android often provide great APIs for your app, you should continue to support older versions of Android until more devices get updated. Generally, it’s a good practice to support about 90% of the active devices, while targeting your app to the latest version. 

###### Platform Versions
The chart below provides data about the relative number of devices running a given version of the Android platform.
![] (https://cloud.githubusercontent.com/assets/10750398/11850985/6bfda560-a441-11e5-87f8-6ff9c6eccab4.jpg)
 
###### Specify Minimum and Target API Levels

When talking about API Level, there are three main attributes to take into consideration:
* ```android:minSdkVersion```

An integer designating the minimum API Level required for the application to run. The Android system will prevent the user from installing the application if the system's API Level is lower than the value specified in this attribute. You should always declare this attribute.

*Caution*: If you do not declare this attribute, the system assumes a default value of "1", which indicates that your application is compatible with all versions of Android. If your application is not compatible with all versions (for instance, it uses APIs introduced in API Level 3) and you have not declared the proper minSdkVersion, then when installed on a system with an API Level less than 3, the application will crash during runtime when attempting to access the unavailable APIs. For this reason, be certain to declare the appropriate API Level in the minSdkVersion attribute.

* ```android:targetSdkVersion```

An integer designating the API Level that the application targets. If not set, the default value equals that given to minSdkVersion.
This attribute informs the system that you have tested against the target version and the system should not enable any compatibility behaviors to maintain your app's forward-compatibility with the target version. The application is still able to run on older versions (down to minSdkVersion). To maintain your application along with each Android release, you should increase the value of this attribute to match the latest API level, then thoroughly test your application on the corresponding platform version.

* ```android:maxSdkVersion```

An integer designating the maximum API Level on which the application is designed to run.
In Android 1.5, 1.6, 2.0, and 2.0.1, the system checks the value of this attribute when installing an application and when re-validating the application after a system update. In either case, if the application's maxSdkVersion attribute is lower than the API Level used by the system itself, then the system will not allow the application to be installed. In the case of re-validation after system update, this effectively removes your application from the device.

Declaring this attribute is not recommended. There is no need to set the attribute as means of blocking deployment of your application onto new versions of the Android platform as they are released. 

Future versions of Android (beyond Android 2.0.1) will no longer check or enforce the maxSdkVersion attribute during installation or re-validation.

For example:
```
<uses-sdk android:minSdkVersion="integer"
          android:targetSdkVersion="integer"
          android:maxSdkVersion="integer" />
```
These attributes can be found and changed in build.gradle file as well. For example:
![] (https://cloud.githubusercontent.com/assets/10750398/11851073/c9525e68-a441-11e5-896a-49b3021faa2c.png)

###### Application forward compatibility
Android applications are generally forward-compatible with new versions of the Android platform. Each successive version of the Android platform can include updates to the Android application framework API that it delivers.
Updates to the framework API are designed so that the new API remains compatible with earlier versions of the API. That is, most changes in the API are additive and introduce new or replacement functionality. As parts of the API are upgraded, the older replaced parts are deprecated but are not removed, so that existing applications can still use them. 
As new versions of Android are released, some style and behaviors may change. To allow your app to take advantage of these changes and ensure that your app fits the style of each user's device, you should set the targetSdkVersion value to match the latest Android version available.

###### Application backward compatibility
Android applications are not necessarily backward compatible with versions of the Android platform older than the version against which they were compiled. Each new version of the Android platform can include new framework APIs, such as those that give applications access to new platform capabilities or replace existing API parts. The new APIs are accessible to applications when running on the new platform and also when running on later versions of the platform, as specified by API Level. Conversely, because earlier versions of the platform do not include the new APIs, applications that use the new APIs are unable to run on those platforms.

Although it's unlikely that an Android-powered device would be downgraded to a previous version of the platform, it's important to realize that there are likely to be many devices in the field that run earlier versions of the platform. Even among devices that receive OTA updates, some might lag and might not receive an update for a significant amount of time.

#### Support Library

In order to provide the best features and functionality across several Android versions, you should use the Android Support Library in your app, which allows you to use several recent platform APIs on older versions. The Android Support Library package is a set of code libraries that provide backward-compatible versions of Android framework APIs as well as features that are only available through the library APIs. Each Support Library is backward-compatible to a specific Android API level. This design means that your applications can use the libraries' features and still be compatible with devices running Android 1.6 (API level 4) and up.

The Support Libraries each target a base Android API level and each provides a different set of features. In order to effectively use the libraries, it is important to consider what features you want to support and understand what features are supported by each library at what Android API level.

Below you can see examples of the Support Library releases:
![] (https://cloud.githubusercontent.com/assets/10750398/11851140/1d296680-a442-11e5-9ddc-85b8d07e6e5b.png)

The support library is imported at the top of a Java file. For example:
![] (https://cloud.githubusercontent.com/assets/10750398/11851177/49814432-a442-11e5-89c4-52ee43d1ed87.png)

###### Check System Version at Runtime
Android provides a unique code for each platform version in the Build constants class. Below is an example of the code to build conditions that ensure the code that depends on higher API levels is executed only when those APIs are available on the system.

```
private void setUpActionBar() {
    // Make sure we're running on Honeycomb or higher to use ActionBar APIs
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.HONEYCOMB) {
        ActionBar actionBar = getActionBar();
        actionBar.setDisplayHomeAsUpEnabled(true);
    }
}
```


#### Questions to discuss:

1. What is the name of the resource folder and resource file where text in the code should be referenced from?
2. Name all the variations of the size and density screen properties on Android.
3. What is the default layout orientaion?
4. How to make an app look differently in the landscape mode?
5. What is the name of the folder where we store images? How many of these folders should an application have?
6. What is an API level?
7. In reference to the API Level which three attributes should be set in the manifest?
8. Look at the Platform Versions Chart and name the latest API? Which API dominates the market?





 









