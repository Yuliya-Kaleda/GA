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




