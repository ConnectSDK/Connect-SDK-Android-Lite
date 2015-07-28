#Connect SDK Android Lite
Connect SDK is an open source framework that connects your mobile apps with multiple TV platforms. Because most TV platforms support a variety of protocols, Connect SDK integrates and abstracts the discovery and connectivity between all supported protocols.
This project can be built in Android Studio or directly with Gradle. Eclipse IDE is not supported since 1.5.0 version.

This repository contains the lite version of the Connect SDK project, and does not include support for platforms that require heavy and/or external dependencies. For the full Connect SDK, clone the [main repository](https://github.com/ConnectSDK/Connect-SDK-Android).

For more information, visit our [website](http://www.connectsdk.com/).

* [General information about Connect SDK](http://www.connectsdk.com/discover/)
* [Platform documentation & FAQs](http://www.connectsdk.com/docs/android/)
* [API documentation](http://www.connectsdk.com/apis/android/)

##Dependencies
This project has the following dependencies.
* [Java-WebSocket library](https://github.com/TooTallNate/Java-WebSocket)
* [Connect-SDK-Android-Core](https://github.com/ConnectSDK/Connect-SDK-Android-Core) submodule

##Including Connect SDK in your app with Android Studio
Edit your project's build.gradle to add this in the "dependencies" section
```groovy
dependencies {
    //...
    compile 'com.connectsdk:connect-sdk-android-lite:1.5.0'
}
```
##Including Connect SDK in your app with Android Studio from sources
1. Open your terminal and execute these commands
    - cd your_project_folder
    - git clone https://github.com/ConnectSDK/Connect-SDK-Android-Lite.git
    - cd Connect-SDK-Android
    - git submodule init
    - git submodule update

2. On the root of your project directory create/modify the settings.gradle file. It should contain something like the following:
    ```groovy
    include ':app', ':Connect-SDK-Android-Lite'
    ```

3. Edit your project's build.gradle to add this in the "dependencies" section:
    ```groovy
    dependencies {
        //...
        compile project(':Connect-SDK-Android-Lite')
    }
    ```

4. Sync project with gradle files
5. Add permissions to your manifest

###Permissions to include in manifest
* Required for SSDP & Zeroconf discovery
 - `android.permission.INTERNET`
 - `android.permission.CHANGE_WIFI_MULTICAST_STATE`
* Required for interacting with devices
 - `android.permission.ACCESS_NETWORK_STATE`
 - `android.permission.ACCESS_WIFI_STATE`
* Required for storing device pairing information
 - `android.permission.WRITE_EXTERNAL_STORAGE`

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
<uses-permission android:name="android.permission.CHANGE_WIFI_MULTICAST_STATE"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

###Proguard configuration
Add the following line to your proguard configuration file (otherwise `DiscoveryManager` won't be able to set any `DiscoveryProvider`).

```
-keep class com.connectsdk.**       { * ; }
```

###Tests
Connect SDK has unit tests for some parts of the code, and we are continuing to increase the test coverage.
These tests are based on third party libraries such as Robolectric, Mockito and PowerMock. You can easily run these tests with Gradle:
```
gradle test
```
Also the project has a target for generating test coverage report with Jacoco. Use this command for generating it.
```
gradle jacocoTestReport
```
The test coverage report will be in this folder `Connect-SDK-Android/build/reports/jacoco/jacocoTestReport/html`.

##Limitations/Caveats

###Subtitles

- DLNA service support `SRT` format only. Since there is no official specification for them, subtitles may not work on all DLNA-compatible devices. This feature has been tested and works on LG WebOS and Netcast TVs.
- Netcast service support `SRT` format only. It uses DLNA and has the same restrictions as DLNA service.

##Contact
* Twitter [@ConnectSDK](https://www.twitter.com/ConnectSDK)
* Ask a question on Stack Overflow with the [Connect-SDK tag](https://stackoverflow.com/tags/connect-sdk) (or [TV tag](https://stackoverflow.com/tags/tv))
* General Inquiries info@connectsdk.com
* Developer Support support@connectsdk.com
* Partnerships partners@connectsdk.com

##Credits
Connect SDK for Android makes use of the following open-source projects.

* [Java-WebSocket](https://github.com/TooTallNate/Java-WebSocket) (MIT)
* [JmDNS](http://jmdns.sourceforge.net) (Apache License, Version 2.0)
* [Android-DLNA](https://code.google.com/p/android-dlna/) (Apache License, Version 2.0)

##License
Copyright (c) 2013-2015 LG Electronics.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

> http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
