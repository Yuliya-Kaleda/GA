### Designing for multiple devices

Android devices come in many shapes and sizes all around the world. With a wide range of device types, you have an opportunity to reach 
a huge audience with your app. In order to be as successful as possible on Android, your app needs to adapt to various device 
configurations. Some of the important variations that you should consider include different languages, screen sizes, and versions of the
Android platform.

#### Supporting Different Languages
It’s always a good practice to extract UI strings from your app code and keep them in an external file. Android makes this easy with 
a resources directory in each Android project. To add support for more languages, create additional values directories inside res/ that 
include a hyphen and the ISO language code at the end of the directory name. For example, values-es/ is the directory containing simple 
resourcess for the Locales with the language code "es". Android loads the appropriate resources according to the locale settings of the 
device at run time. The folder structure will look like this:

![](https://cloud.githubusercontent.com/assets/10750398/11787045/d1075c76-a257-11e5-9850-9337d7d28476.png)

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
* density: low (ldpi), medium (mdpi), high (hdpi), extra high (xhdpi)
To declare different layouts and bitmaps you'd like to use for different screens, you must place these alternative resources in separate directories, similar to how you do for different language strings.

###### Create Different Layouts
To optimize user experience on different screen sizes, you should create a unique layout XML file for each screen size you want to support. Each layout should be saved into the appropriate resources directory, named with a ```-<screen_size>``` suffix. For example:

![](https://cloud.githubusercontent.com/assets/10750398/11787480/e1db3fac-a259-11e5-9874-de95420af6a3.png)

 This project includes a default layout and an alternative layout for large screens. The file names must be exactly the same, but their contents are different in order to provide an optimized UI for the corresponding screen size.
 Also be aware that the screens orientation (landscape or portrait) is considered a variation of screen size, so many apps should revise the layout to optimize the user experience in each orientation. By default, the layout xml files are used for portrait orientation. To reference a lanscape orientation, the folder should add the suffis -land. 
 
 ![](https://cloud.githubusercontent.com/assets/10750398/11794335/cd4f40f4-a27e-11e5-8fa4-2ea7a2f81316.png)
 
 ###### Create Different Bitmaps
 
All bitmap resources should be properly scaled to each of the generalized density buckets: low, medium, high and extra-high density. To generate images, you should start with your raw resource in vector format and generate the images for each density using the following size scale:

xhdpi: 2.0
hdpi: 1.5
mdpi: 1.0 (baseline)
ldpi: 0.75

After the images are ready, they are placed in the appropriate drawable resource directory. For example:

![](https://cloud.githubusercontent.com/assets/10750398/11794684/98b1926e-a280-11e5-8dbf-6750034c1b0a.png)
 
Any time you reference @drawable/android.png, the system selects the appropriate bitmap based on the screen's density.



 









