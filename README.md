arcgis-android-sdk-module
=========================

ArcGIS Runtime SDK for Android library module for Android Studio.  Use the version library module, e.g. ```arcgis-android-v10.2.3``` to convert your android project into an ArcGIS Android project.

# Fork the repo
If you haven't already, go to https://github.com/ArcGIS/arcgis-android-sdk-module and click the **Fork** button.

# Clone the repo
Open your terminal, navigate to your working directory, use ```git clone``` to get a copy of the repo.

```
$ git clone git@github.com:YOUR-USERNAME/arcgis-android-sdk-module.git
```
# Integrate into existing Android Project
You can integrate the ArcGIS Android lib module into an existing Android project.

## Update Manifest
The ```Android.manifest``` file is now located in the ```/src/main/``` directory of your application project.

- Double click the  manifest file to open it.  Add the following to your manifest:

```
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />

<uses-feature
    android:glEsVersion="0x00020000"
    android:required="true" />
```

