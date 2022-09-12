[![](https://raw.githubusercontent.com/shuftipro/RESTful-API-v1.2/master/assets/banner.jpg)](https://www.shuftipro.com/)

# ShuftiPro NFC SDK

Shufti Pro’s API supports verification with and without OCR. 
## Table of contents
* [General Requirements](#general-requirements)
* [Permissions](#permissions)
* [SDK Installation Guide](#sdk-installation-guide)
* [SDK Version](#sdk-version)
* [JSON Object](#json-object-with-ocr)



# Basic Setup
## General Requirements
Followings are minimum requirements for SDK:
- iOS 13.0 and higher
- Internet connection

Supported architectures in SDK:
- armv7 and arm64 for devices

## Permissions:
* ### Application Info.plist must contain an **Privacy - Camera Usage Description** , **Privacy - Microphone Usage Description**  and  **Privacy - NFC Scan Usage Description**key with a explanation to end-user about how the app uses this data.
* ### And Open your Info.plist file as Source Code add these lines inside dict tag.
```
<key>com.apple.developer.nfc.readersession.iso7816.select-identifiers</key>
<array>
    <string>00000000000000</string>
    <string>A0000002471001</string>
</array>
```
* ### In your Project target add under Signing and Capabilities section tap on Capabilities and add Near Field communication Tag Reading.
For more guidance watch this guided image. [here](nfcGuide.png)


## SDK Installation Guide
1. Add these dependencies into your project's pod file.
```
    pod 'NFCPassportReader', git:'https://github.com/AndyQ/NFCPassportReader.git'
    pod 'GoogleMLKit/TextRecognition'
    
```
Please make sure to add the following post-install hook to your Podfile.

```
post_install do |installer|
  installer.pods_project.targets.each do |target|
    if ['NFCPassportReader'].include? target.name
      target.build_configurations.each do |config|
          config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
      end
    end
  end
end


```

2. Copy “ShuftiPro.framework” into your project folder.
3.  In xcode select your project -> your project under TARGETS -> General -> Embeded Binaries
4.  Add “ShuftiPro.framework” in Embeded Binaries.
5. Make sure your in your xcode project build settings "Validate Workspace" is set to "Yes"


## SDK Version:
Currently our updated SDK version is 3.3.0

## Integration: 
See the sample project provided to learn the most common use. Make sure to build on real device.
```sh
import ShuftiPro
```
## JSON Object With Ocr
```sh
        "document": [
                ... 

                "nfc_verification": "false",
        ]
```


# Request Parameters

  
  * <h3>nfc_verification</h3>

  Required: **No**  
  Type: **boolean**  
  Accepted values:  **true**, **false**  

Near Field Communication (NFC) is a set of short-range wireless technologies. NFC allows sharing small payloads of data between an NFC tag and an NFC-supported device. NFC Chips found in modern passports and similar identity documents contain additional encrypted information about the owner. This information is very useful in verifying the originality of a document. NFC technology helps make the verification process simple, quicker and more secure. This also provides the user with contactless and input less verification. ShuftiPros's NFC verification feature detects MRZ from the document to authenticate NFC chip and retrieve data from it, so the authenticity and originality of the provided document could be verified, if set to TRUE. nfc_verification parameter should be added into the service object **(document, document_two, address)** for which you want to perform nfc verification. Nfc verification is allowed only on e-passports under document, document_two and address service only. The nfc service is not available in hybrid webview for now.
  
Other parameters are explained [here](https://github.com/shuftipro/iOS-SDK#auth-keys).
