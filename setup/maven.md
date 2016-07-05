# Maven setup instructions
## Windows setup
### 1. JDK setup
Make sure JDK is installed, and '`JAVA_HOME`' variable is added as Windows environment variable. [**Here**](https://github.com/MusalaSoft/atmosphere-docs/blob/master/setup/jdk.md) you may read **how to setup JDK**.

### 2. Download and install Apache Maven
* Visit [Maven official website](http://maven.apache.org/), download the Maven binary zip archive. Unzip it to the folder you want to install Maven. Assume you unzip to this folder – `C:\apache-maven-[version]`

* These steps are Windows 7 specific, but are almost the same for Windows XP/8/8.1/10

 * Open the start menu and right clock on 'Computer' -> Properties.

 * Choose Advanced System Settings -> Environment variables.

 * In 'System variables' select 'New...' button and add variable with name `MAVEN_HOME` and value the full path to Maven installation folder (for instance: `C:\apache-maven-[version]`).

 * In 'System variables' find Path variable. Append to Path value the string `%MAVEN_HOME%\bin`. You might need to add a '`;`' before the new string to separate it from the previous one (if '`;`' is not available at the end of Path value).

* To verify Maven installation, run `mvn –version` in the command prompt.
```
$ mvn -version
Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-10T18:41:47+02:00)
Maven home: C:\apache-maven-3.3.9
Java version: 1.8.0_91, vendor: Oracle Corporation
Java home: C:\Program Files\Java\jdk1.8.0_91\jre
Default locale: en_US, platform encoding: Cp1251
OS name: "windows 7", version: "6.1", arch: "amd64", family: "dos"
```
If you see a similar message, means the Apache Maven is installed successfully on Windows.
