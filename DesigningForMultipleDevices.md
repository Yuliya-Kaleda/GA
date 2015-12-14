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

![](https://cloud.githubusercontent.com/assets/10750398/11786265/9ea49d9c-a253-11e5-92cb-a4cf2cb46968.png)

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
    ```TextView textView = (TextView) findViewById(R.id.view);
        textView.setText(R.string.program);```






