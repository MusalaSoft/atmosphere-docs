# ATMOSPHERE mobile testing framework
## Installation instructions
The instructions for installation could be found [here](installation.md).
## Overview
Atmosphere is a black-box testing framework for native android applications. One of the advantages of our solution is that we do not need the code of the application being tested, it is sufficient to provide the installation file that is available on the markets of the certain mobile platform. Atmosphere is easy to integrate with other third party testing tools like TestNG and Selenium. The users (testers) can configure which tests are going to be executed on what kind of devices. They can also specify that some tests need to be run on multiple different in parameters devices simultaneously.
Here is a short list of mobile specific things that can be tested with our framework:
 * Resource exhaustion - mobile devices are still with more limited hardware parameters and thus they are a lot more easily subject to resource exhaustion, for example the device can run out of battery.
 * Complex interactions - in scrollable views, time and date pickers, notification bar. The fact that smart phones go with touch screen displays allow for a lot more complex interaction with them. Using such interaction technique is far more intuitive to human beings, but is very hard to simulate using software, thus making testing a lot harder.
 * Gestures - swiping, tapping, clear and input text.
 * Complex selectors - elements on screen can be selected both with XPath and CSS expressions.
 * Manipulation of hardware sensors such as position sensors (magnetic field) and motion sensors (device acceleration).
 * Setting device orientation.
 * Setting GPS coordinates.
 * Checking WiFi connection, camera availability and GPS coordinates.
 * Sending, receiving and answering calls.

We really believe we provide a product focused primarily on the specifics of mobile testing, allowing for automating all these weird scenarios that you can not test with any contemporary testing tool. We have already succeeded automating a lot greater percentage of the test scenarios for our own mobile applications than what we were able beforehand.
