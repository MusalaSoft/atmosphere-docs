# Debugging a Gradle project with Eclipse

#### Install Gradle
You need to have `gradle` installed (where the Java program is running - the host machine)

#### Setting up gradle debug configuration for all projects
* Add this `init.gradle` file in your `$HOME/.gradle` directory:

  ```java
  allprojects {
      tasks.withType(Test) {
          if (System.getProperty('DEBUG', 'false') == 'true') {
              jvmArgs '-Xdebug',
                  '-Xrunjdwp:transport=dt_socket,server=y,suspend=y,address=9009'
          }
      }

      tasks.withType(JavaExec) {
          if (System.getProperty('DEBUG', 'false') == 'true') {
              jvmArgs '-Xdebug',
                  '-Xrunjdwp:transport=dt_socket,server=y,suspend=y,address=9009'
          }
      }
  }
  ```

* Import the gradle project in Eclipse. You may use plugins like Gradle STS or Buildship.

#### Create a new Remote Java Application configuration.
  * Open Eclipse and go to `Run -> Debug Configurations...`.
  * Select the Remote Java Application in the list of configuration types on the left.
  * Click the `New` toolbar button. A new remote launch configuration is created and three tabs are shown: `Connect`, `Source`, and `Common`.
  * In the `Project` field of the `Connect` tab, type or browse to select the project to use as a reference for the launch (for source lookup).
  * In the Host field of the `Connect` tab, type the IP address or domain name of the host where the Java program is running. If the program is running on the same machine as the workbench, type `localhost`.
  * In the `Port` field of the `Connect` tab, type the port where the remote VM is accepting connections. In our case the port will be `9009`.
  * Click `Apply`.

#### Enable gradle Debug
 * For `test` task debugging run `$ gradle -DDEBUG=true test` on console.
 * For `run` task debugging run `$ gradle -DDEBUG=true run` on console.

Now you can use your Eclipse debugger to debug ATMOSPHERE project.
