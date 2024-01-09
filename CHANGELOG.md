## 1.31.7
* **[Fix]** `cancelWhenScanComplete` must handle error cases

## 1.31.6
* **[Feature]** add `cancelWhenScanComplete` convenience function

## 1.31.5
* **[Improve]** Updated README & Example app

## 1.31.4
* **[Fix]**  iOS: mtu and auto connect are incompatible

## 1.31.3
* **[Fix]**  `adapterState.first` & `connectionState.first` dont work (regression 1.30.7)

## 1.31.2
* **[Fix]** Gradle 7 (Flutter 2) would not build (regression 1.7.6)

## 1.31.1
* **[Fix]**  iOS: scan filters were doing nothing (regression 1.31.0)

## 1.31.0
This release adds support for multiple scan filters at the same time.
* **[Feature]** iOS: support multiple scan filters at the same time

## 1.30.9
* **[Improve]** assert: fbp only supprts a single `scan` filter at a time

## 1.30.8
* **[Improve]** android: discoverServices: add `subscribeToServicesChanged` option

## 1.30.7
* **[Fix]** `autoConnect` not always working (bug in 1.30.0)
* **[Fix]**  perf: `NewStreamWithInitialValue` was not closing its streams (regression 1.17.2)
* **[Feature]** add `device.isAutoConnectEnabled`

## 1.30.6
* **[Improve]** ios log more detail
* **[Feature]** add `adapterStateNow` getter

## 1.30.5
* **[Fix]** iOS build error (regression 1.30.4)
* **[Fix]** android `autoConnect` was broken (regression 1.30.1)

## 1.30.4
* **[Fix]** Perf: must close `adapterState`, `bondState` & `scanResults` BufferStreams
* **[Improve]** iOS: set `kCBConnectOptionEnableAutoReconnect` option
* **[Improve]** requestMtu: add `predelay` argument
* **[Example]** only call `setState` if mounted

## 1.30.3

* **[Fix]** android: connect crashes (regression in 1.30.0)

## 1.30.2
* **[Improve]** auto connect: assert that mtu is null in `connect`

## 1.30.1
* **[Feature]** auto connect: remove `setAutoConnect` function added in 1.30.0 and go back to using `connect:autoConnect` parameter

## 1.30.0
This release greatly improves `autoconnect` support on Android, and adds iOS support.
* **[Improve]** android: auto connect is no longer canceled when bluetooth is turned off
* **[Fix]** android: `deadObjectExceptions` when bluetooth is turned off

## 1.29.13
* **[Improve]**  android: add delay before `requestMtu` is called to work around `discoverServices` timeout

## 1.29.12
* **[Fix]** android: `CALLBACK_TYPE_FIRST_MATCH` causes scanning issues (regression in 1.27.0)
* **[Fix]** android: `withKeywords` wasn't filtering out adverts that have no scan record (bug in original feature)

## 1.29.11
* **[Fix]** android: `remoteId` was wrong (regression in 1.29.10)

## 1.29.10
* **[Fix]** android: `isNotifying` was not updated (regression in 1.28.5)
* **[Improve]** accidentally logging 'canceling connection in progress' every time

## 1.29.9
* No changes. This version was accidentally skipped.

## 1.29.8
* **[Fix]** android: crash due to wrong type cast (regression in 1.29.7)

## 1.29.7
* **[Fix]** scan errors should be pushed to `scanResults` stream (bug in original `flutter_blue`)
* **[Fix]** android: scan: when `continuousUpdates` is `false`, don't filter non-duplicate adverts (bug in original feature)
* **[Improve]** make sure `continuousDivisor` only applies when `continuousUpdates` is true

## 1.29.6
* **[Improve]** default `continuousDivisor` should be 1
* **[Improve]** `continuousDivisor` should be applied after scan filters

## 1.29.5
* **[Fix]**  iOS: 'service not found' if service supports short uuid (regression 1.28.5)
* **[Improve]**  android: handle `turnOn` user rejected

## 1.29.4
* **[Fix]** characteristics with same UUID could return wrong `properties` or `descriptors` (regression in 1.20.4)

## 1.29.1 to 1.29.3
* **[Improve]** more refinements to `onScanResults`

## 1.29.0
* **[Breaking Change]** `scanResults`: do not clear results after `stopScan`. If you want results cleared use `onScanResults` instead.
* **[Add]** `lastScanResults` to synchronously get the most recent results

## 1.28.14
* **[Fix]** `setAdvertisingDataType` crash on android 10 and below (regression in 1.28.10)

## 1.28.13
* **[Fix]** `isNotifying` was not set to false on disconnection (regression in 1.28.9)

## 1.28.12
* **[Fix]** crash if `rssi` was zero on android (regression in 1.27.2)

## 1.28.11
* **[Rename]** `giud.uuid` -> `guid.str` & `guid.uuid128` -> `guid.str128`
* **[Add]** connect: `timeout` argument is now optional. infinite timeout is possible on iOS

## 1.28.10
* **[Perf]** android: filter out devices without names if `scan.withKeywords` is set
* **[Fix]** calling scan multiple times would breifly push `isScanning=false`
* **[Improve]** `servicesList`: return empty instead of null

## 1.28.9
* **[Improve]** to make FBP easier to use, never clear `knownServices`

## 1.28.8
* **[Fix]** android: GUID issues related to scanning (regression in 1.28.3)

## 1.28.7
* **[Fix]** android: GUID starting with 0000 were misinterpretted (regression in 1.28.5)

## 1.28.6
* **[Improve]** simplify api: clear `knownServices` on reconnection instead of disconnection
* **[Improve]** dont clear `bondState` cache when device is disconnected. unecessary.

## 1.28.5
* **[Internal]** use short UUID where possible

## 1.28.4
* **[Fix]** guid: uuid was returning 0000 for 16 bit uuid (regression in 1.28.3)
* **[Guid]** `guid.uuid` should return lowercase

## 1.28.3
* **[Improve]** guid: add `uuid` short representation

## 1.28.2
* **[Improve]** add length checks to `MsdFilter` & `ServiceDataFilter`
* **[Improve]** guid: more consistent handling of 16, 32, vs 128 bit guids

## 1.28.1
* **[Feature]** scanning: add `withServiceData` filter
* **[Feature]** scanning: add `withMsd` filter

## 1.28.0
* **[Breaking Change]** `guid.toString()` now returns 16-bit short uuid when possible
* **[Breaking Change]** return `GUID`s for `advertisingData.serviceUuids` & `advertisingData.serviceData` instead of String
* **[Guid]** add support for 16-bit and 32-bit uuids
* **[Fix]** android: advertised UUIDs were 128-bit instead of the actual length (regression in 1.14.17)

## 1.27.6
* **[Improve]** add more checks for bluetooth being off

## 1.27.5
* **[Fix]** android: typo compile error (regression in 1.27.3)

## 1.27.4
* **[Fix]** accidentally changed `advertisementData.localName` to nullable (regression in 1.27.3)

## 1.27.3
* **[Perf]** scanning: add `continuousDivisor` option to reduce platform channel & main-thread usage

## 1.27.2
* **[Perf]** scanning: only send advertisment keys over platform channel when they exist
* **[Rename]** `advertisementData.localName` -> `advertisementData.advName`

## 1.27.1
* **[Add]** android: add `forceIndications` option to `setNotifyValue`

## 1.27.0
This release improves the default scanning behavior.
* **[Breaking Change]** scanning: make `continousUpdates` false by default - it is not typically needed & hurts perf. If your app uses `startScan.removeIfGone`, or your app continually checks the value of `scanResult.timestamp` or `scanResult.rssi`, then you will need to explicitly set `continousUpdates` to true.

## 1.26.6
* **[Fix]** android: scanning would not work if `continuousUpdates` was false  (regression in 1.26.5)

## 1.26.5
* **[Add]** scanning: `withRemoteIds`, `withNames`, `withKeywords` filters
* **[Add]** scanning: expose `androidScanMode` again
* **[Add]** scanning: `continuousUpdates` option replaces former `allowDuplicates` option

## 1.26.4
* **[Add]** `cancelWhenDisconnected`: option to cancel on *next* disconnection

## 1.26.3
* **[Add]** `events.onReadRssi`
* **[Add]** `events.onCharacteristicWritten`
* **[Add]** `events.onDescriptorWritten`

## 1.26.2
* **[Fix]** android: close gatt after canceling an in-progress connnection  (regression in 1.26.1)
* **[Improve]** android: wait until bonding completes for better reliability

## 1.26.1
* **[Feature]** add support for canceling an in progress connection using `device.disconnect`
* **[Fix]** connection timeouts did not actually cancel the connection attempt (regression in 1.5.0)
* **[Fix]** android: update `isScanning` when `onDetachedFromEngine` is called (bug in original `flutter_blue`)

## 1.22.1 to 1.26.0
These releases changed multiple things but then changed them back. For brevity, here are the actual changes:
* **[Behavior Change]** android: listen to Services Changed characteristic to match iOS behavior
* **[Fix]** android: stop scanning when detached from engine (bug in original `flutter_blue`)
* **[Add]** `device.advName` returns the name found during scanning
* **[Add]** `device.mtuNow` synchronously gets the current mtu value
* **[Add]** `events.onDiscoveredServices` stream
* **[Add]** events api: add accessors for errors
* **[Rename]** events api: most functions & classes were renamed for consistency
* **[Rename]** `device.onServicesChanged` -> `device.onServicesReset`
* **[Remove]** `device.onNameChanged`, in favor of only exposing `events.onNameChanged`

## 1.22.0
This release makes `mtu` behavior more similar on android & iOS.
* **[Breaking Change]** android: request mtu of 512 by default.

## 1.21.0
This release greatly increases reliability on android & ios.
* **[Improve]** only allow a single ble operation at a time.

## 1.20.8
* **[Fix]** iOS: connect: return error for invalid `remoteId`  (bug in original `flutter_blue`)
* **[Improve]** iOS: log warning if CCCD is not found, like we do on android

## 1.20.7
* **[Fix]**  events API was not accessible through `FlutterBluePlus.events`

## 1.20.6
* **[Add]** `FlutterBluePlus.events.mtu`

## 1.20.5
* **[Add]** `FlutterBluePlus.events.onNameChanged`
* **[Add]** `FlutterBluePlus.events.onServicesChanged`

## 1.20.4
* **[Rename]** `FlutterBluePlus.connectionEvents` -> `FlutterBluePlus.events.connectionState`
* **[Add]** `FlutterBluePlus.events.onCharacteristicReceived`
* **[Add]** `FlutterBluePlus.events.onDescriptorRead`
* **[Add]** `FlutterBluePlus.events.bondState`

## 1.20.3
* **[Add]** `FlutterBluePlus.connectionEvents`, a stream of all connection & disconnected events
* **[Add]** `FlutterBluePlus.connectedDevices`, to get currently connected devices
* **[Add]** `device.isConnected`, convenience accessor

## 1.20.2
* **[Fix]** cannot retrieve platform name from `bondedDevices`  (regression)
* **[Fix]** `stopScan`: should clear results *after* platform method has been called  (bug in original `flutter_blue`)

## 1.20.1
* **[Remove]** `FlutterBluePlus.connectedDevices`. This API needs more thought.

## 1.20.0
This release renames `connectedSystemDevices`.
* **[Rename]** `connectedSystemDevices` -> `systemDevices`, because they must be re-connected by *your* app

## 1.19.2
* **[Add]** new method `device.cancelWhenDisconnected(subscription)`

## 1.19.1
* **[Add]** new method `FlutterBluePlus.connectedDevices`

## 1.19.0
This release reverts most of the breaking changes made in 1.18.0.
* **[Revert]** most breaking changes made to `bondState` stream in 1.18.0
* **[Unchanged]** bond lost/failed are replaced by `prevBondState`
* **[Add]** method `device.prevBondState`
* **[Fix]** android: `adapterName` must request permission  (bug in original `flutter_blue`)

## 1.18.3
* **[Refactor]** `bondState`: finish refactor started in 1.18.0

## 1.18.2
* **[Fix]** `bondState`: must *explicitly* check for null `prevState` (regression in 1.18.0)

## 1.18.1
* **[Fix]** `bondState`: handle null `prevState` (regression in 1.18.0)

## 1.18.0
This release improves `bondState` stream
* **[Breaking Change]** `bondState`: directly expose `prevBond` instead of lost/failed flags

## 1.17.6
* **[Fix]** `scanResults`: clear scan results on `stopScan` (regression in 1.16.8)

## 1.17.5
* **[Example]** accidentally left `performanceOverlay` enabled (regression in 1.17.4)

## 1.17.4
* **[Example]** remove `PermissionHandler` dependency. It is no longer needed.
* **[Example]** ScanScreen: use `ListView` instead of `SingleChildScrollView`

## 1.17.3
* **[Fix]** android: `turnOn` throws exception if permission denied  (bug in original `flutter_blue`)

## 1.17.2
This bug affected `mtu`, `lastValueStream`, `adapterState`, & `bondState`.
* **[Fix]** `newStreamWithInitialValue` was not emitting initial value. (regression in 1.16.6)

## 1.17.1
* **[Fix]** timeout when `connect` is called when adapter is off (bug in original `flutter_blue`)
* **[Fix]** android: was not calling `disconnect` callback when adapter turned off (bug in original `flutter_blue`)
* **[Fix]** android: `connectable` flag was not working (regression in 1.7.0)
* **[Improve]** do not re-get `adapterState` when we already have it

## 1.17.0
This release improves `lastValue` & `lastValueStream`.
* **[Breaking Change/Fix]** should update `lastValue` & `lastValueStream` when `write` is called
* **[Feature]** Android: support `onNameChanged` & `onServicesChanged` characteristics
* **[Fix]** iOS: `discoverServices` crash "[_NSInlineData intValue]: unrecognized selector sent to instance" (bug in original `flutter_blue`)
* **[Fix]** iOS: `descriptor.write` would timeout or not work (regression somewhere around ~1.7.0)
* **[Fix]** `isNotifying` was not updated by `setNotifyValue(false)` (regression somewhere around ~1.9.0)

## 1.16.12
* **[Fix]** Android: `onValueReceived` was not working on Android 12 & lower (regression in 1.16.3)

## 1.16.11
* **[Fix]** Android: `onCharacteristicReceived` not being called (regression in 1.16.3)

## 1.16.10
* **[Fix]** BluetoothDevice: don't wait for timeout if device becomes disconnected (bug in original `flutter_blue`)

## 1.16.9
* **[Example]** cleaned up Characteristic tile code

## 1.16.8
* **[Fix]** `scanResults` & `isScanning` streams were not re-emitting their current value on listen (regression in 1.5.0)
* **[Example]** `discoverServices`: stay on screen after diconnection
* **[Example]** simplified `connectingOrDisconnecting` code
* **[Example]** organize into 'screens' and 'widgets' folders

## 1.16.7
* **[Rename]** `isAvailable` -> `isSupported`

## 1.16.6
* **[Example]** Refactor: hugely refactored to use stateful widgets
* **[Example]** Fix: stream already listened to error
* **[Improve]** `connectionState` & `mtu`: use broadcast stream

## 1.16.5
* **[Fix]** iOS: iOS Unhandled Exception: type 'int' is not a subtype of type 'bool' (regression in 1.16.3)
* **[Improve]** android: prepend logs with '[FBP]'
* **[Java]** rename `com.boskokg.flutter_blue_plus` -> `com.lib.flutter_blue_plus` to be more generic

## 1.16.4
* **[Fix]** `setLogLevel` would be ignored due to being called twice (regression in 1.10.0)
* **[Improve]** android: use log level consistently
* **[Improve]** iOS: use log level macro

## 1.16.3
* **[Fix]** Android: `setNotify` would timeout if CCCD descriptor does not exist (regression in 1.5.0)
* **[Android]** fix deprecations
* **[Improve]** `removeIfGone`: only push to scanResults when list changes

## 1.16.2
* **[Fix]** platform check in `onNameChanged` & `onServicesChanged` was incorrect

## 1.16.1
* **[Add]** iOS: add support for `onServicesChanged` & `onNameChanged`

## 1.16.0
This release simplifies BluetoothDevice construction.
* **[Breaking Change]** remove `BluetoothDevice.type` & `BluetoothDevice.localName` from constructor for simplicity
* **[Breaking Change]** remove `servicesStream` & `isDiscoveringServices` deprecated functions
* **[Rename]** `localName` -> `platformName` to reflect platform specific behavior
* **[Fix]** `setNotifyValue` must take `descWrite` mutex (bug in original `flutter_blue`)
* **[Fix]** `localName` was broken when using `connectedSystemDevices` (regression in 1.15.10)
* **[Add]** Android: `getPhySupport`

## 1.15.10
* **[Fix]** iOS: `localName` does not match Android (bug in original `flutter_blue`)
* **[Fix]** flutterHotRestart: error was thrown if device did not have bluetooth adapter (regression in 1.14.19)

## 1.15.9
* **[Fix]** iOS: adapter turnOff: edge case when adapter is turned off while scanning (bug in original `flutter_blue`)
* **[Fix]** iOS: adapter turnOff: disconnect handlers not firing when adapter turned off (bug in original `flutter_blue`)
* **[Fix]** iOS: adapter turnOff: API MISUSE when adapter is turned off (bug in original `flutter_blue`)
* **[Cleanup]** Hot Restart: use separate `connectedCount` method for clarity

## 1.15.8
* **[Fix]** if any platform exception happens, fbp will deadlock (regression in 1.14.20)

## 1.15.7
* **[Fix]** android: turning bluetooth off would not fully disconnect devices (regression in 1.14.19)

## 1.15.6
* **[Fix]** iOS: turning bluetooth off would not fully disconnect devices (regression in 1.14.19)
* **[Readme]** add v1.15.0 migration guides

## 1.15.5
* **[Fix]** `firstWhereOrNull` conflict (regression in 1.15.0)

## 1.15.4
* **[Fix]** some typos in disconnect exceptions (regression in 1.15.3)

## 1.15.3
* **[Improve]** prefer dart exceptions over platform exceptions when device is disconnected

## 1.15.2
* **[Fix]** `stopScan` was not awaiting for invokeMethod (regression in 1.15.0)

## 1.15.1
* **[Fix]** `FlutterBluePlus.scanResults` should always return list copy to avoid iteration exceptions (regression in 1.15.0)

## 1.15.0
## Scanning API Changes

**Overview**:
* **[Refactor]** simplify scanning api
* **[Feature]** add `removeIfGone` option to `startScan`

**Breaking Changes & Improvements:**
- **(simplify)** removed `FlutterBluePlus.scan`. Use `FlutterBluePlus.scartScan(oneByOne: true)` instead.
- **(simplify)** removed `allowDuplicates` option for `scartScan`. It is not supported on android. We always filter duplicates anyway.
- **(simplify)** removed `macAddresses` option for `scartScan`. It was not supported on iOS, and is overall not very useful.
- **(simplify)** `startScan` now returns `Future<void>` instead of `Future<List<ScanResult>>`. It was redundant and confusing.
- **(improvement)** if you `await startScan` it will complete once the scan starts, instead of when it ends
- **(improvement)** if you call `startScan` twice, it will cancel the previous scan, instead of throwing an exception

## 1.14.24
* **[Fix]** Android: `setNotifyValue`: "(code: 5) notifications were not updated" (regression in 1.14.23)
* **[Fix]** Hot Restart: stop scanning when hot restarting (bug in original `flutter_blue`)

## 1.14.23
* **[Fix]** `setNotifyValue` & others must be cleared after disconnection (regression in 1.14.21)

## 1.14.22
* **[Fix]** Android: Hot Restart: could get stuck in infinite loop (regression in 1.14.19)

## 1.14.21
* **[Refactor]** dart: store `lastValue` at global level so Desc & Chr classes are fully immutable

## 1.14.20
* **[Fix]** iOS: Hot Restart: could get stuck in infinite loop (regression in 1.14.19)

## 1.14.19
* **[Fix]** Hot Restart: close all connections when dart vm is restarted (bug in original `flutter_blue`)

## 1.14.18
* **[Fix]** Android: crash `uuid128` null deref (regression in 1.14.17)

## 1.14.17
* **[Fix]** Android: shortUUID: characteristic not found (bug in original `flutter_blue`)

## 1.14.16
* **[Fix]** macOS: lower required version to 10.11 (equivalent to  iOS 9.0)

## 1.14.15
* **[Rename]** `allowSplits` -> `allowLongWrite`

## 1.14.14
* **[Fix]** Android: "dataLen longer than allowed" (regression in 1.14.13)

## 1.14.13
* **[Fix]** iOS: onMtu was not called (bug in original `flutter_blue`)
* **[Feature]** iOS & Android: `writeCharacteristic`: add `allowLongWrite` option to do longer writes

## 1.14.12
* **[Feature]** support harmony