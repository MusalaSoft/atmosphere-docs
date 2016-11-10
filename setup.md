# Setup
## Prerequisites
 * [Install JDK and set JAVA_HOME as an Environment variable](/setup/jdk.md)
 * [Download Android SDK and set ANDROID_HOME as an Environment variable](/setup/android_sdk.md)

## Quick-run
1. Download the Agent and Server run script bundle and extract it to a convenient location: [atmosphere-framework.zip](https://github.com/MusalaSoft/atmosphere-docs/releases/latest)

1. Run the Server by executing the following command in the directory from the previous step:  
 * `gradlew runServer` (on Windows)
 * `./gradlew runServer` (on Linux/macOS)

 Wait until you see an output similar to this:
 ```
 com.musala.atmosphere.server.state.RunningServer$InnerRunThread.run(RunningServer.java:47) 24 Aug 2016 11:08:49 - Running Server...
 ```
 Leave the Terminal open.

1. Connect a physical device or run an Android emulator.

1. In a new Command Prompt/Terminal run the Agent by executing the following command in the directory from Step 1:  
 * `gradlew runAgent` (on Windows)
 * `./gradlew runAgent` (on Linux/macOS)

 Wait until you see an output similar to this:  
 ```
 com.musala.atmosphere.agent.AgentManager.createWrapperForDevice(AgentManager.java:378) 24 Aug 2016 12:53:43 - Created wrapper for device with bindingId = 0149BCA70C01D00F
 ```

You are now set to [run Atmosphere tests](https://github.com/MusalaSoft/atmosphere-docs#atmosphere-tests).

## Additional options
The Quick-run setup is useful if you like to setup the Atmosphere framework on a single machine or to quickly start using it on a new machine from the ground up. More options are available for a fine grained setup of the framework. You are also able to run only a single task on the current machine to set up only the corresponding component on it.

### Server Port
By default the Server will run on port 1980. If you would like to change the port, open the `server.properties` file in a text editor and change the value of the `pool.manager.rmi.port` property before you run the Server.

### Agent - Server automatic connection
The Agent will attempt to connect to a Server automatically when run. By default it uses `localhost` and the value of the `pool.manager.rmi.port` in the `server.properties` file as arguments. You can change this behavior by providing these arguments with the run command:
```
./gradlew runAgent [-Pip=<ip address of the Server>] [-Pport=<port of the Server>]
```

None of these arguments are required. If an argument is not provided, the default value will be used.
