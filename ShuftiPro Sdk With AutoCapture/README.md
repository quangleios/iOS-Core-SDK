[![](https://raw.githubusercontent.com/shuftipro/RESTful-API-v1.2/master/assets/banner.jpg)](https://www.shuftipro.com/)

# ShuftiPro Auto Capture SDK

## Table of contents
* [General Requirements](#general-requirements)
* [Permissions](#permissions)
* [SDK Installation Guide](#sdk-installation-guide)
* [SDK Version](#sdk-version)
* [Integration](#integration)
* [Config Object Parameters ](#config-object-parameters)


# Basic Setup
## General Requirements
Followings are minimum requirements for SDK:
- iOS 13.0 and higher
- Internet connection

Supported architectures in SDK:
- armv7 and arm64 for devices

## Permissions:
* ### Application Info.plist must contain an **Privacy - Camera Usage Description** , **Privacy - Microphone Usage Description** 


## SDK Installation Guide
1. Add these dependencies into your project's pod file.
```
    pod 'GoogleMLKit/TextRecognition'
    pod 'TensorFlowLiteSwift'
```
2. Copy “ShuftiPro.framework” into your project folder.
3.  In xcode select your project -> your project under TARGETS -> General -> Embeded Binaries
4.  Add “ShuftiPro.framework” in Embeded Binaries.



## SDK Version:
Currently our updated SDK version is 3.3.0


## Integration: 
See the sample project provided to learn the most common use. Make sure to build on real device.

## Configs
```sh
  let configs = [
              ... 
              "autoCapture" : true,
                
  ]
```

# Config Object Parameters
In this object, we add extra configuration of verification that the user wants.

* ## autoCapture

    Required: **No**  
    Type: **boolean** <br>
  Accepted Values: **true**, **false**  

    AutoCapture provides click-less capturing of required objects. If **autoCapture** value is set to **TRUE** it would capture the image without the need of clicking button. AutoCapture is available for face, document/ document- two(passport, id card, driving license, credit or debit card) and address. The user would also be able to capture manually while auto capture is set to true. If **autoCapture** is set to **FALSE** then the user must capture the image by clicking capture button. The document will only be captured if it matches with the provided country and document type as well, otherwise error will be shown.
  <br>

  Other parameters are explained [here](https://github.com/shuftipro/iOS-SDK#auth-keys).


