# Ant setup instructions
## Windows
### Install Ant
 1. Download Ant from the official [website](http://ant.apache.org/bindownload.cgi). It should be a zip archive.
 2. Unpack it to a suitable location, preferably `C:\apache-ant-[version]`.

### Add Ant to the System Path
These steps are Windows 7 specific, but are almost the same for Windows XP/8/8.1/10

 * Open the Start menu and right click on 'Computer' -> Properties.

 * Choose Advanced system settings -> Environment variables.

 * In 'System variables' click 'New...' and add a variable with name `ANT_HOME` and value of the full path to the Ant folder (example: `C:\apache-ant-1.9.7`).

 * Find 'Path' in 'System variables', select it and click 'Edit...'. Append `%ANT_HOME%\bin` to the end. You may have to use a `;` as a delimiter from the previous entry.

Now open a command prompt and run `ant -version`. You should get an output similar to this one:
```
Apache Ant(TM) version 1.9.7 compiled on April 9 2016
```

## Linux/macOS
Just use the package manager to install `ant`.
