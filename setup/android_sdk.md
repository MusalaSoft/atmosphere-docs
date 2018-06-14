# Android SDK setup instructions
## Android SDK
If you already have Android Studio installed, most likely you also have Android SDK. If you don't have a local Android SDK installation, you can download it from [here](https://developer.android.com/studio/index.html#downloads).
You don't need the whole bundle, so look for files whose names start with `sdk-tools-` and choose the one appropriate for your system. Extract the archive to a suitable location after the download is complete. For example, `%userprofile%\android-sdk\` (for Windows) or `~/android-sdk/` (for Linux/macOS).

You will need the following packages:

* **Android SDK Tools**
* **Android SDK Platform-tools**
* **Android SDK Build-tools** - `v25`
* **Android 7.1.1 (API 25)**:
  * **SDK Platform**

If you are using Android Studio, you can use the integrated SDK Manager to download and install them. You can then skip to the [Set ANDROID_HOME](#set-android_home) section below. If not, you can use the command line tools you downloaded earlier. The following steps are for the command line tools only.

Go to `tools/bin/` and install the required packages:

* **Windows** Run `sdkmanager.bat "tools" "platform-tools" "build-tools;25.0.0" "platforms;android-25"`
* **Linux/macOS** Run `./sdkmanager "tools" "platform-tools" "build-tools;25.0.0" "platforms;android-25"`

## Set ANDROID_HOME
After the Android SDK is ready to use, you need to set a system path variable pointing to the Android SDK directory.

**Windows** These steps are Windows 7 specific, but are almost the same for Windows XP/8/8.1/10

 * Open the Start menu and right click on 'Computer' -> Properties.

 * Choose Advanced system settings -> Environment variables.

 * In 'System variables' click 'New...' and add a variable with name `ANDROID_HOME` and value of the full path to the Android SDK folder (for instance: `%userprofile%\android-sdk`).

**Linux** Open the file `~/.profile` and add the following line to the end of it: `export ANDROID_HOME=[path-to-android-sdk]`. Log out and in again for the changes to take effect.
