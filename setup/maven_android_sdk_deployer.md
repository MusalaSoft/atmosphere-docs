# Maven Android SDK Deployer setup instructions
The ATMOSHPERE mobile testing framework uses libraries which are part of the Android SDK.
Since the Android SDK license does not allow us to distribute these libraries separately,
we need to extract the libraries from your local Android SDK installation first. There is a nice tool that could do just that: [Maven Android SDK Deployer][1].

## Requirements

### Android SDK
You will need the following components installed:

 * **Android SDK Tools**
 * **Android SDK Platform-tools**
 * **Android SDK Build-tools** - `v23.0.3`
 * **Android 4.4.2 (API 19)**:
   * **SDK Platform**
   * **Google APIs**
   * **Glass Development Kit Preview**

You can find more info on how to install and configure the Android SDK [here][2].
### Set ANDROID_HOME
After the Android SDK is ready to use, you need to set a system path variable pointing to the Android SDK directory.

**Windows** These steps are Windows 7 specific, but are almost the same for Windows XP/8/8.1/10

 * Open the Start menu and right click on 'Computer' -> Properties.

 * Choose Advanced system settings -> Environment variables.

 * In 'System variables' click 'New...' and add a variable with name `ANDROID_HOME` and value of the full path to the Android SDK folder (for instance: `%userprofile%\android-sdk`).

**Linux** Open the file `~/.profile` and add the following line to the end of it: `export ANDROID_HOME=[path-to-android-sdk]`. Log out and in again for the changes to take effect.

### Maven
Currently the tool depends on Maven, so you must have Maven installed. Installation instructions can be found [here][3], but keep an eye on the Maven Android SDK Deployer documentation as these requirements might change in the future.

## Usage
Download the Maven Android SDK Deployer from the GitHub repository (or `git clone` it): [Maven Android SDK Deployer][1].

For the ATMOSPHERE projects you only need to export `v4.4.2` of the library. This can be done by running the command `mvn install -P 4.4` in the root directory of the Maven Android SDK Deployer.

If the build is successful, you are all set.

[1]: https://github.com/simpligility/maven-android-sdk-deployer
[2]: android_sdk.md
[3]: maven.md
