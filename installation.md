# Installation
## Prerequisites
1. [Install JDK and set JAVA_HOME as an Environment variable](/setup/jdk.md)
1. [Download Android SDK and set ANDROID_HOME as an Environment variable](/setup/android_sdk.md)

## ATMOSPHERE
1. Clone the following repositories from https://github.com/MusalaSoft/:
  * ```atmosphere-commons```
  * ```atmosphere-agent-device-lib```
  * ```atmosphere-server-agent-lib```
  * ```atmosphere-client-server-lib```
  * ```atmosphere-bitmap-comparison```
  * ```atmosphere-ime```
  * ```atmosphere-service```
  * ```atmosphere-uiautomator-bridge```
  * ```atmosphere-client```
  * ```atmosphere-agent```
  * ```atmosphere-server```

  You can clone all of them using a single command.  
  * For Windows use:
  ```
  git clone https://github.com/MusalaSoft/atmosphere-commons.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-agent-device-lib.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-server-agent-lib.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-client-server-lib.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-bitmap-comparison.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-ime.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-service.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-uiautomator-bridge.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-client.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-agent.git && ^
  git clone https://github.com/MusalaSoft/atmosphere-server.git
  ```
  * For Linux/macOS use:
  ```
  git clone https://github.com/MusalaSoft/atmosphere-commons.git && \
  git clone https://github.com/MusalaSoft/atmosphere-agent-device-lib.git && \
  git clone https://github.com/MusalaSoft/atmosphere-server-agent-lib.git && \
  git clone https://github.com/MusalaSoft/atmosphere-client-server-lib.git && \
  git clone https://github.com/MusalaSoft/atmosphere-bitmap-comparison.git && \
  git clone https://github.com/MusalaSoft/atmosphere-ime.git && \
  git clone https://github.com/MusalaSoft/atmosphere-service.git && \
  git clone https://github.com/MusalaSoft/atmosphere-uiautomator-bridge.git && \
  git clone https://github.com/MusalaSoft/atmosphere-client.git && \
  git clone https://github.com/MusalaSoft/atmosphere-agent.git && \
  git clone https://github.com/MusalaSoft/atmosphere-server.git
  ```

1. Build and publish each project to your local Maven repository. This can be done with a single command.

 For Windows use:
 ```
 cd atmosphere-commons && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-agent-device-lib && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-server-agent-lib && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-client-server-lib && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-bitmap-comparison && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-ime && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-service && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-uiautomator-bridge && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-client && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-agent && gradlew build && gradlew publishToMavenLocal && cd .. && ^
 cd atmosphere-server && gradlew build && gradlew publishToMavenLocal && cd ..
 ```

 For Linux/macOS use:
 ```
 cd atmosphere-commons && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-agent-device-lib && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-server-agent-lib && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-client-server-lib && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-bitmap-comparison && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-ime && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-service && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-uiautomator-bridge && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-client && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-agent && ./gradlew build && ./gradlew publishToMavenLocal && cd .. && \
 cd atmosphere-server && ./gradlew build && ./gradlew publishToMavenLocal && cd ..
 ```

 Alternatively you can build each project separately by running in the project's root directory:
  * ```gradlew build``` (on Windows)
  * ```./gradlew build``` (on Linux/macOS)  
 and if the build is successful, you can publish it to you local Maven repository using:
  * ```gradlew publishToMavenLocal``` (on Windows)
  * ```./gradlew publishToMavenLocal``` (on Linux/macOS)

1. Run the Server by executing the following command in the `atmosphere-server` root directory:  
 * ```gradlew run``` (on Windows)
 * ```./gradlew run``` (on Linux/macOS)

 Wait until you see an output similar to this:
 ```
 ...
 >> 05 XII 2016 15:21:05 - Running Server...
The Server has started successfully.
 ```
 Leave the Terminal open.

1. Connect a physical device or run an Android emulator.

1. In a new Command Prompt/Terminal run the Agent by executing the following command in the `atmosphere-agent` root directory:  
 * ```gradlew run``` (on Windows)
 * ```./gradlew run``` (on Linux/macOS)

 Wait until you see an output similar to this:  
 ```
 ...
 05 XII 2016 15:36:03 - Agent created on port: 1989
 The Agent has started successfully.
>>
 ```

1. Connect the Agent to the Server by running ```connect <port>``` in the Agent Terminal. By default the Server port is set to ```1980```. It could be changed by editing the ```pool.manager.rmi.port``` property in the ```server.properties``` file in the ```atmosphere-server``` root directory.

You should now be set to [run Atmosphere tests](https://github.com/MusalaSoft/atmosphere-docs#atmosphere-tests).
