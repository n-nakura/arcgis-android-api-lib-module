# Overview
ArcGIS Android API library module for Android Studio. Use the version library module, e.g. ```arcgis-android-v10.2.3``` to convert your android project into an ArcGIS Android project, create a new ArcGIS Android project, or work with the [ArcGIS Android SDK Gradle sample modules](https://github.com/ArcGIS/arcgis-android-sdk-gradle-samples).

# Early Access Preview
**Caution:** arcgis-android-api-lib-module is currently available as an **early access preview** for use with [Android Studio](http://developer.android.com/sdk/installing/studio.html).  If you are not comfortable using an unfinished product, you may want to use the Eclipse Plugin bundled with the [ArcGIS Android SDK](https://developers.arcgis.com/android/).

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

## Import ArcGIS Android lib module
This is where we start to turn our project into an ArcGIS for Android project.

### Direct Import
- Right Click your project and select **Open Module Settings**
- Click the ```+``` sign above **SDK Location** and select **Import Existing Project** then click **Next**
- Navigate to the folder where you cloned the ```arcgis-android-sdk-module``` repo and select the ```arcgis-android-v10.2.3``` folder which contains the library module.  Do not import the entire project, just the library module e.g. ```/[path-to-repo]/arcgis-android-sdk-module/arcgis-android-v10.2.3``` and click **OK** then **Finish** to import the library module.

**NOTE** If you navigate to the root project directory you will see all available modules listed.  Check the ```arcgis-android-v10.2.3``` module to select it from your project.

### Add ArcGIS library module dependency to your app
- Double click on your applications ```build.gradle``` file to open it in the editor.  This will be the file at the root of your application modules directory.
- Add ```compile project(":arcgis-android-v10.2.3")``` to your dependencies:

```
dependencies {
    // Add this dependency
    compile project(":arcgis-android-v10.2.3")

    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.android.support:appcompat-v7:19.+'
}
```

- Add the following exclusions above ```buildTypes```

```
    packagingOptions{
        exclude 'META-INF/LGPL2.1'
        exclude 'META-INF/LICENSE'
        exclude 'META-INF/NOTICE'
    }
```

- Click the **Sync Project with Gradle Files** button from the toolbar.

### Make the ArcGIS module
- Right click the ```arcgis-android-10.2.3``` module and select **Make Module 'arcgis-android-v10.2.3'**.
- Double click the ArcGIS library module's ```build.gradle``` file to open in editor.  This will the file at the root of your ArcGIS library module.
- Uncomment the following:

```
    ndk{
        moduleName "libruntimecore_java"
    }
```

- Click the **Sync Project with Gradle Files** button from the toolbar.
- This should throw the following error: ```Error:(14, 0) Build script error, unsupported Gradle DSL method found: 'ndk()'!```
- Re-comment the ```ndk``` task.
- Click the **Sync Project with Gradle Files** button from the toolbar.

You should now see all the ArcGIS libs in the **External Libraries** drop down. **NOTE** You may need to do the first step again to see the libs.

You should now be ready to start coding with ArcGIS Runtime SDK for Android!
