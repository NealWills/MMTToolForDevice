# MMTToolForDevice

[![CI Status](https://img.shields.io/travis/Donghn/MMTToolForDevice.svg?style=flat)](https://travis-ci.org/Donghn/MMTToolForDevice)
[![Version](https://img.shields.io/cocoapods/v/MMTToolForDevice.svg?style=flat)](https://cocoapods.org/pods/MMTToolForDevice)
[![License](https://img.shields.io/cocoapods/l/MMTToolForDevice.svg?style=flat)](https://cocoapods.org/pods/MMTToolForDevice)
[![Platform](https://img.shields.io/cocoapods/p/MMTToolForDevice.svg?style=flat)](https://cocoapods.org/pods/MMTToolForDevice)

## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements

## Installation

MMTToolForDevice is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'MMTToolForDevice'
```

## How To Use

#### use

```Swift
class Class {
    func startDFU() {
        let startAddressStr = "01080000"

	MMTToolForGoodixDFUTool.addDelegate(self)
  
	MMTToolForGoodixDFUTool.startDfu(deviceUUID: device.uuid, deviceMac: device.mac, deviceMacExtra: device.macExtra, peripheral: device.peripheral, startAddress: startAddressStr, filePath: filePath)
    }

}

extension Class: MMTToolForGoodixDFUDelegate {
    func mmtToolForGoodixUnitDidShowErrorMessage(_ unit: MMTToolForGoodixDFU.MMTToolForGoodixDFUToolUnit?, stage: String?, error: (any Error)?) {
  
    }

    func mmtToolForGoodixUnitDidEnter(_ unit: MMTToolForGoodixDFU.MMTToolForGoodixDFUToolUnit?) {

    }

    func mmtToolForGoodixUnitDidFailToEnter(_ unit: MMTToolForGoodixDFU.MMTToolForGoodixDFUToolUnit?, error: (any Error)?) {
  
    }
  
    func mmtToolForGoodixUnitDFUDidBegin(_ unit: MMTToolForGoodixDFU.MMTToolForGoodixDFUToolUnit?) {
  
    }
  
    func mmtToolForGoodixUnitDFUDidChangeProgress(_ unit: MMTToolForGoodixDFU.MMTToolForGoodixDFUToolUnit?, progress: Int) {
  
    }
  
    func mmtToolForGoodixUnitDFUDidEnd(_ unit: MMTToolForGoodixDFU.MMTToolForGoodixDFUToolUnit?, error: (any Error)?) {
  
    }
  
    func mmtToolForGoodixUnitGetUUID(_ unit: MMTToolForGoodixDFU.MMTToolForGoodixDFUToolUnit?) -> DFUServerTurple? {
        let device = ....
        let service = device.serviceList[.goodixService]
        let readCharacter = device.characterList[.goodixCharactericsRxUUid]
        let writeCharacter = device.characterList[.goodixCharactericsTxUUid]
        let controlCharacter = device.characterList[.goodixCharactericsControlPointUUid]
        return ( service: service, readCharacter: readCharacter, writeCharacter: writeCharacter, controlCharacter: controlCharacter )
    }

}
```

#### Dealloc

```
MMTToolForGoodixDFUTool.removeDelegate(self)
```

## Author

Donghn, Donghn@maxeye.com

## License

MMTToolForDevice is available under the MIT license. See the LICENSE file for more info.
