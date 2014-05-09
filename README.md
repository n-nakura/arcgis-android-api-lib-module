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

## Update Projects Gradle build
In this step we want to ensure that your project is using the latest Gradle plugin.  Gradle plugins are on a different release cycle then Android Studio so you may have to manually update until Android Studio directly supports the latest version of Gradle plugin.

- Double click on your projects ```build.gradle``` file to open it in the editor.  This will be the one at the project root directory, not in your application directory.
- Ensure that under ```dependencies``` you have the following classpath

```
    dependencies {
        classpath 'com.android.tools.build:gradle:0.10.+'
    }
```

- Click the **Sync Project with Gradle Files** button from the toolbar.

Gradle Plugin v0.10.0 is the latest version of the Gradle Plugin at the time of the writing so the version will change as more releases come out.
