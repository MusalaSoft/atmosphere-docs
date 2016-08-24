# Installation
## Prerequisites
1. [Install JDK and set JAVA_HOME as an Environment variable](/setup/jdk.md)
1. [Download Android SDK and set ANDROID_HOME as an Environment variable](/setup/android_sdk.md)
1. [Install Maven and setup the Maven Android SDK Deployer](/setup/maven_android_sdk_deployer.md)

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

1. Export the Android SDK library:  
 The `atmosphere-commons` project depends on a library which is part of the Android SDK. The Android SDK license does not allow us to distribute Android SDK libraries separately, so we need to extract the libraries from your local Android SDK installation. You can find instructions on how to do this [here](https://github.com/MusalaSoft/atmosphere-docs/blob/master/setup/maven_android_sdk_deployer.md).

1. Following the order of the above list, run:  
 ```gradlew build``` (on Windows) or ```./gradlew build``` (on Linux/macOS),  
 and if the build is successful:  
 ```gradlew publishToMavenLocal``` (on Windows) or ```./gradlew publishToMavenLocal``` (on Linux/macOS)  
 in the root directory of each of the downloaded repositories.

 For Windows you can build all project using this single command:
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

 For Linux/macOS use this command:
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

1. Run the Server by executing the following command in the `atmosphere-server` root directory:  
 * ```gradlew run``` (on Windows)
 * ```./gradlew run``` (on Linux/macOS)

 Wait until you see an output similar to this:
 ```
 >> com.musala.atmosphere.server.state.RunningServer$InnerRunThread.run(RunningServer.java:47) 24 Aug 2016 11:08:49 - Running Server...
 ```
 Leave the Terminal open.

1. Connect a physical device or run an Android emulator.

1. Download [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/downloads) and unzip it in a convenient directory. Open ```agent.properties``` in the ```atmosphere-agent``` and change the value of the property ```chromedriver.executable.path``` to point to the ChromeDriver executable.

1. In a new Command Prompt/Terminal run the Agent by executing the following command in the `atmosphere-agent` root directory:  
 * ```gradlew run``` (on Windows)
 * ```./gradlew run``` (on Linux/macOS)

 Wait until you see an output similar to this:  
 ```
 com.musala.atmosphere.agent.AgentManager.createWrapperForDevice(AgentManager.java:378) 24 Aug 2016 12:53:43 - Created wrapper for device with bindingId = 0149BCA70C01D00F
 ```

1. Connect the Agent to the Server by running ```connect <port>``` in the Agent Terminal. By default the Server port is set to ```1980```. It could be changed by editing the ```pool.manager.rmi.port``` property in the ```server.properties``` file in the ```atmosphere-server``` root directory.

You should now be set to [run Atmosphere tests](https://github.com/MusalaSoft/atmosphere-docs#atmosphere-tests).
