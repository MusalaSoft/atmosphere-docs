# JDK setup instructions

## Windows setup

* Use [**this link**](http://www.oracle.com/technetwork/java/javase/downloads/index.html?ssSourceSiteId=otnjp ) to download JDK.

* Start the downloaded exe file and install JDK to the default  location. Remember this location path because you will need it in next  steps.

* These steps are Windows 7 specific, but are almost the  same for Windows XP/8/8.1/10

 * Open the start menu and right clock on 'Computer'  -> Properties.
 
 * Choose Advanced System Settings -> Environment variables.
 
 * In  'System variables' select 'New...' button and add variable with name `JAVA_HOME` and value the full path to JDK installation folder.
 
 * In  'System variables' find Path variable. Append to Path value the string  `%JAVA_HOME%\bin`. You might need to add a '`;`' before the new string to  separate it from the previous one (if '`;`' is not available at the end of  Path value).
 
* To verify javac is in the PATH, run `java -version` in the command prompt.
```
$ java -version
java version "1.8.0_91"
Java(TM) SE Runtime Environment (build 1.8.0_91-b15)
Java HotSpot(TM) 64-Bit Server VM (build 25.91-b15, mixed mode)
```
If you see a similar message, means the JDK is installed successfully on Windows.