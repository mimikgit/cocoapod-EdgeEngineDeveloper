# ``EdgeEngine``

mimik Client Library provides a programmatic way to work with the edgeEngine Runtime to access information about the mobile device on which the application is running.

@Metadata {
    @CallToAction(purpose: link, url: "https://github.com/mimikgit/cocoapod-EdgeEngine")
    @PageKind(article)
    @PageColor(orange)
}


## Overview

The purpose of the **mimik Client Library for iOS** is to provide a programmatic way to work with the edgeEngine Runtime to access information about the mobile device on which the application is running, as well as mobile devices running within a cluster of mobile devices that are hosting the edgeEngine Runtime. Also, to allow developers to use edge microservices running within a particular cluster.

The **mimik Client Library for iOS suite** consists of three individual cocoapod components:

    - EdgeCore
    - EdgeEngineDeveloper (or EdgeEngine for enterprise solutions) 
    - EdgeUser

By leveraging the **`EdgeCore cocoapod component`**, developers can build applications compatible with the edgeEngine Runtime.

Additionally, this component provides utility APIs that help developers with core operations such as Authentication, edgeEngine Runtime Setup, deployment of edge microservices and handling of network calls.

Furthermore, the **`EdgeEngineDeveloper (or EdgeEngine for enterprise solutions) cocoapod component`** provides edgeEngine Runtime lifecycle control API, as well as vendoring the actual edgeEngine Runtime binary into the iOS project.

Expanding the client library ecosystem is the **`EdgeUser cocoapod component`**, providing API for integrating mimik Hybrid Edge Cloud edge and backend microservices.


## Supported Platforms, Targets
* `iOS Devices running iOS 15+`
* `iOS Simulators running iOS 15+`
* `iOS Mac Catalyst running macOS 12.0`


## Requirements
```
iOS 15.0+
```

## Installation

To install `EdgeCore` and `EdgeEngineDeveloper (or EdgeEngine for enterprise solutions)` cocoapods simply add the following lines to your Podfile:

> **_NOTE:_** Developers wanting to use their **developer edge license** from [mimik developer console](https://developer.mimik.com/console) should specify  [EdgeEngineDeveloper](https://github.com/mimikgit/cocoapod-EdgeEngineDeveloper) cocoapod in their `Podfile`.

> **_NOTE:_** Enterprise developers should specify [EdgeEngine](https://github.com/mimikgit/cocoapod-EdgeEngine) cocoapod in their `Podfile` and use the **full edge license** they received from [mimik support](https://developer.mimik.com/support/).


```swift
platform :ios, '15.0'
source 'https://github.com/CocoaPods/Specs.git'
source 'https://github.com/mimikgit/cocoapod-edge-specs.git'

use_frameworks!
inhibit_all_warnings!

def mimik
  pod 'EdgeCore'
  pod 'EdgeEngineDeveloper'
  ### or pod 'EdgeEngine' (see the two notes above)
end

target '{target}' do
  mimik()
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['ENABLE_BITCODE'] = 'NO'
      config.build_settings['VALID_ARCHS'] = '$(ARCHS_STANDARD_64_BIT)'
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '15.0'
      config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
    end
  end
end
```

## Tutorials

After installation, try the following tutorials:

- [Integrating the mimik Client Library into an iOS project](https://devdocs.mimik.com/tutorials/11-index)
- [Working with edgeEngine in an iOS project](https://devdocs.mimik.com/tutorials/12-index)
- [Working with edge microservices in an iOS project](https://devdocs.mimik.com/tutorials/13-index)
- [Creating a Simple iOS Application that Uses an edge microservice](https://devdocs.mimik.com/tutorials/10-index)


## Documentation

`EdgeCore/EdgeClient` API reference documentation can be found  [online](https://mimikgit.github.io/cocoapod-EdgeCore/documentation/edgecore/edgeclient). Alternatively a docc archive file can be downloaded as a [zip file](https://github.com/mimikgit/cocoapod-EdgeCore/tree/main/EdgeCore.doccarchive.zip) and opened locally in Xcode.

`EdgeEngineClient` platform protocol API reference documentation can also be found [online](https://mimikgit.github.io/cocoapod-EdgeCore/documentation/edgecore/edgeengineclient).

`EdgeUserClient` platform protocol API reference documentation can be found [online](https://mimikgit.github.io/cocoapod-EdgeCore/documentation/edgecore/edgeuserclient) as well.

## mimik client libraries

Explore all mimik client libraries [available on Github](https://github.com/search?q=cocoapod-Edge).

Cocoapod sets:

* [EdgeClientLibraryDeveloper = (EdgeCore + EdgeEngineDeveloper)](https://github.com/mimikgit/cocoapod-EdgeClientLibraryDeveloper)
* [EdgeClientLibrary = (EdgeCore + EdgeEngine)](https://github.com/mimikgit/cocoapod-EdgeClientLibrary)
 
Cocoapod individual pods:
 
* [EdgeCore](https://github.com/mimikgit/cocoapod-EdgeCore)
* [EdgeEngineDeveloper](https://github.com/mimikgit/cocoapod-EdgeEngineDeveloper)
* [EdgeEngine](https://github.com/mimikgit/cocoapod-EdgeEngine)
* [EdgeUser](https://github.com/mimikgit/cocoapod-EdgeUser)


## Author

[mimik Technology, Inc.](https://mimik.com)

More details about how the edgeEngine platform revolutionizes computing with the hybrid-cloud approach are at [mimik Developer Documentation](https://devdocs.mimik.com).


## License

Developers can get their developer edge license by following this [tutorial](https://devdocs.mimik.com/tutorials/02-index).

For details about a full edge license please contact [mimik support](https://mimik.com/contact-us/).
