# JDK setup instructions

## Windows
* [Download JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html?ssSourceSiteId=otnjp). The Atmosphere framework supports JDK 7 or newer.

* Start the downloaded exe file and install JDK. Remember the location path because you will need it in the next steps.

* These steps are Windows 7 specific, but are almost the same for Windows XP/8/8.1/10

 * Open the start menu and right click on `Computer -> Properties`

 * Choose `Advanced System Settings -> Environment variables`

 * In `System variables` click the `New...` button and add variable with name `JAVA_HOME` and the value of the full path to the JDK installation folder.

 * In `System variables` find the `Path` variable. Append to the `Path` value the string `%JAVA_HOME%\bin`. You might need to add a `;` before the new string to separate it from the previous one (if `;` is not present at the end of Path value).

* To verify javac is in the PATH, run `java -version` in the command prompt.
```
$ java -version
java version "1.8.0_91"
Java(TM) SE Runtime Environment (build 1.8.0_91-b15)
Java HotSpot(TM) 64-Bit Server VM (build 25.91-b15, mixed mode)
```
If you see a similar message, the JDK is installed successfully on Windows.

## Linux
 * You can use [OpenJDK](http://openjdk.java.net/install/) or [Oracle JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) (version 7 or newer)
 * Add the `JAVA_HOME` variable to `~/.profile` or `~/.bash_profile`:
 ```
 export JAVA_HOME=[path-to-jdk]
 ```
 * Restart the session to have the changes take effect.

## macOS
 * [Download JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) (version 7 or newer) and follow these [instructions](https://docs.oracle.com/javase/8/docs/technotes/guides/install/mac_jdk.html) to install it OR use [Homebrew](http://brew.sh/):
```
brew update
brew cask install java
```
 * Instructions on how to set the `JAVA_HOME` environment variable on macOS can be found [here](https://www.mkyong.com/java/how-to-set-java_home-environment-variable-on-mac-os-x/).
