#Connect SDK Android Lite
Connect SDK is an open source framework that connects your mobile apps with multiple TV platforms. Because most TV platforms support a variety of protocols, Connect SDK integrates and abstracts the discovery and connectivity between all supported protocols.

This repository contains the lite version of the Connect SDK project, and does not include support for platforms that require heavy and/or external dependencies. For the full Connect SDK, clone the [main repository](https://github.com/ConnectSDK/Connect-SDK-Android).

For more information, visit our [website](http://www.connectsdk.com/).

* [General information about Connect SDK](http://www.connectsdk.com/discover/)
* [Platform documentation & FAQs](http://www.connectsdk.com/docs/android/)
* [API documentation](http://www.connectsdk.com/apis/android/)

##Dependencies
This project has the following dependencies.
* [Java-WebSocket library](https://github.com/TooTallNate/Java-WebSocket)
* [Connect-SDK-Android-Core](https://github.com/ConnectSDK/Connect-SDK-Android-Core) submodule

##Including Connect SDK in your app

1. Setup up your dependencies, listed above
2. Clone Connect-SDK-Android-Lite project (or download & unzip)
3. Open Eclipse
4. Click File > Import
5. Select `Existing Android Code Into Workspace` and click Next
6. Browse to the Connect-SDK-Android-Lite project folder and click Open
7. Click Finish
8. Right-click the Connect-SDK-Android-Lite project and select Properties
9. In the Library pane of the Android tab, add the following library references
   - Connect-SDK-Android-Core
10. **You must update these libraries to API 10 in their manifest.**
11. Click OK
12. Right-click your project and select Properties
13. In the Library pane of the Android tab, add the Connect-SDK-Android-Lite project
14. Set up your manifest file as per the instructions below

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

##Contact
* Twitter [@ConnectSDK](https://www.twitter.com/ConnectSDK)
* Ask a question with the "tv" tag on [Stack Overflow](http://stackoverflow.com/tags/tv)
* General Inquiries info@connectsdk.com
* Developer Support support@connectsdk.com
* Partnerships partners@connectsdk.com

##Credits
Connect SDK for Android makes use of the following open-source projects.

* [Java-WebSocket](https://github.com/TooTallNate/Java-WebSocket) (MIT)
* [JmDNS](http://jmdns.sourceforge.net) (Apache License, Version 2.0)
* [Android-DLNA](https://code.google.com/p/android-dlna/) (Apache License, Version 2.0)

##License
Copyright (c) 2013-2014 LG Electronics.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

> http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
