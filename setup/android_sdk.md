# Android SDK setup instructions
## Android SDK
If you already have Android Studio installed, most likely you also have Android SDK. If you don't have a local Android SDK installation, you can download it from [here](https://developer.android.com/studio/index.html#downloads).
You don't need the whole bundle, so look for files whose names start with `android-sdk_` and choose the one appropriate for your system. Extract the archive to a suitable location after the download is complete.

Start the SDK Manager.  

* **Windows** Run `SDK Manager.exe` in the main SDK directory.  
* **Linux/macOS** Run `android` in `[android-sdk]/tools`

After the SDK Manager finishes loading install the following components:

 * **Android SDK Tools**
 * **Android SDK Platform-tools**
 * **Android SDK Build-tools** - `v25`
 * **Android 7.1.1 (API 25)**:
   * **SDK Platform**

## Set ANDROID_HOME
After the Android SDK is ready to use, you need to set a system path variable pointing to the Android SDK directory.

**Windows** These steps are Windows 7 specific, but are almost the same for Windows XP/8/8.1/10

 * Open the Start menu and right click on 'Computer' -> Properties.

 * Choose Advanced system settings -> Environment variables.

 * In 'System variables' click 'New...' and add a variable with name `ANDROID_HOME` and value of the full path to the Android SDK folder (for instance: `%userprofile%\android-sdk`).

**Linux** Open the file `~/.profile` and add the following line to the end of it: `export ANDROID_HOME=[path-to-android-sdk]`. Log out and in again for the changes to take effect.
