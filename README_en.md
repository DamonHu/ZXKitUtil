# ZXKitUtil

![](https://img.shields.io/badge/CocoaPods-supported-brightgreen) ![](https://img.shields.io/badge/Swift-5.0-brightgreen) ![](https://img.shields.io/badge/License-MIT-brightgreen) ![](https://img.shields.io/badge/version-iOS10.0-brightgreen)

[中文文档](./README.md)

`ZXKitUtil` is a collection of commonly used functions, which integrates common functions simply and efficientl.

OC version: [HDCommonTools](https://github.com/DamonHu/HDCommonTools)

## import the project

### Import via cocoapods

```
pod 'ZXKitUtil'
```

If you need the function of `idfa`, you can choose to import

```
pod 'ZXKitUtil/idfa'
```

### Import via file

Download the project and import the contents of the `pod` folder under the project file into the project

## API list

Existing data type operations can be used through the syntax of `.zx`, and other operations can be used through the singleton of `ZXKitUtil.shared`.

* There is no difference between singleton and `.zx`, singleton will be more unified and simple. The advantage of `.zx` syntax is that it does not need to be imported where it is used

### UI related

|Name|Function description|Example|
|----|----|----|
|func getCurrentNormalWindow()|Get the current NormalWindow|ZXKitUtil.shared.getCurrentNormalWindow()|
|func getCurrentVC()|Get the current ViewController|ZXKitUtil.shared.getCurrentVC()|
|func getImage(color: UIColor)|Generate a solid color background image by color|ZXKitUtil.shared.getImage(color: UIColor.red) <br/>or<br/> UIImage.zx.getImage(color: UIColor .red)|
|func getLinearGradientImage(colors: [UIColor], directionType: ZXKitUtilGradientDirection, size: CGSize = CGSize(width: 100, height: 100))|Generate a linear gradient image|ZXKitUtil.shared.getLinearGradientImage(colors: [UIColor.red , UIColor.black, UIColor.blue] <br/>or<br/> UIImage.zx.getLinearGradientImage(colors: [UIColor.red, UIColor.black, UIColor.blue], directionType: .leftToRight)|
|func getRadialGradientImage(colors: [UIColor], raduis: CGFloat, size: CGSize = CGSize(width: 100, height: 100))|Generate an angular gradient image|ZXKitUtil.shared.getRadialGradientImage(colors: [UIColor.red , UIColor.black, UIColor.blue], raduis: 45) <br/> or<br/> UIImage.zx.getRadialGradientImage(colors: [UIColor.red, UIColor.black, UIColor.blue], raduis: 45)|
|func getColor(hexString: String, alpha: CGFloat = 1.0)|Get color by hexadecimal string| UIColor.zx.color(hexString: "#FFFFFF")|
|func UIColor(hexValue: Int, darkHexValue: Int = 0x333333, alpha: Float = 1.0, darkAlpha: Float = 1.0)|Get color by hexadecimal| UIColor.zx.color(hexValue: 0xffffff)|
|UIScreenWidth|Screen width||
|UIScreenHeight|Screen height||
|ZXKitUtil_StatusBar_Height|Status Bar height||
|ZXKitUtil_HomeIndicator_Height|Home Indicator height||
|func ZXKitUtil_Default_NavigationBar_Height(vc: UIViewController? = nil)|Navigation Bar Height|ZXKitUtil_Default_NavigationBar_Height()|
|func func ZXKitUtil_Default_Tabbar_Height(vc: UIViewController? = nil)|tabbar height|ZXKitUtil_Default_Tabbar_Height()|
|func addLayerShadow(color: UIColor, offset: CGSize, radius: CGFloat, cornerRadius: CGFloat? = nil)|Add a shadow to the view|view.zx.addLayerShadow(color: UIColor.black, offset: CGSize(width: 2, height : 0), radius: 10)|
|func setFrame(x: CGFloat? = nil, y: CGFloat? = nil, width: CGFloat? = nil, height: CGFloat? = nil)|view individually sets a certain value of Frame|view.zx.setFrame(x: 10)|
|func className() -> String| get view's class name|button.zx.className()|

### System and software information

|Name|Function description|Example|
|----|----|----|
|func getAppVersionString()|Get software version|ZXKitUtil.shared.getAppVersionString()|
|func getAppBuildVersionString()|Get software build version|ZXKitUtil.shared.getAppBuildVersionString()|
|func getAppNameString()|get app's Name|ZXKitUtil.shared.getAppNameString()|
|func getIOSVersionString()|Get the iOS version of the system|ZXKitUtil.shared.getIOSVersionString()|
|func getIOSLanguageStr()|Get system language|ZXKitUtil.shared.getIOSLanguageStr()|
|func getBundleIdentifier()|Get Software Bundle Identifier|ZXKitUtil.shared.getBundleIdentifier()|
|func getSystemHardware()|Get the machine model identification|ZXKitUtil.shared.getSystemHardware()|
|func getSystemUpTime()|Get the last restart time of this machine|ZXKitUtil.shared.getSystemUpTime()|
|func getIDFAString(idfvIfFailed: Bool = true)|The unique identification of the simulation software|ZXKitUtil.shared.getIDFAString()|
|func getMacAddress()|To get the MAC address of the mobile phone WIFI, you need to enable Access WiFi information|ZXKitUtil.shared.getMacAddress()|
|func openSystemSetting()|Open system settings|ZXKitUtil.shared.openSystemSetting()|
|func openAppStorePage(openType: ZXKitUtilOpenAppStoreType, appleID: String)|Open the App Store page corresponding to the software|ZXKitUtil.shared.openAppStorePage(openType: .app, appleID: "1123211")|
|func openAppStoreReviewPage(openType: ZXKitUtilOpenAppStoreType, appleID: String = "")|Open the score page corresponding to the software|ZXKitUtil.shared.openAppStoreReviewPage(openType: .app)|

### Software permissions

|Name|Function description|Example|
|----|----|----|
|func requestPermission(type: ZXKitUtilPermissionType, complete: @escaping ((ZXKitUtilPermissionStatus) -> Void))|Request permission|ZXKitUtil.shared.requestPermission(type: .notification) {(status) in print("Permission setting callback" , status) }|
|func checkPermission(type: ZXKitUtilPermissionType, complete: @escaping ((ZXKitUtilPermissionStatus) -> Void))|Checking software permissions|ZXKitUtil.shared.checkPermission(type: .notification) {(status) in print("Current permission status ", status) }|
|func requestIDFAPermission(complete: @escaping ((ZXKitUtilPermissionStatus) -> Void)) -> Void|request idfa permission|ZXKitUtil.shared.requestIDFAPermission {(status) in print("Current idfa permission status", status)} |
|func checkIDFAPermission(type: ZXKitUtilPermissionType, complete: @escaping ((ZXKitUtilPermissionStatus) -> Void)) -> Void|check software idfa permission|ZXKitUtil.shared.checkIDFAPermission {(status) in print("Current Permission Status", status) }|

### Multimedia operation

|Name|Function description|Example|
|----|----|----|
|func getVideoDuration(videoURL: URL) -> Double|Get the duration of the specified video, in seconds | ZXKitUtil.shared.getVideoDuration(videoURL: URL(fileURLWithPath: path))|
|func getVideoSize(videoURL: URL)|Get the specified video resolution, support local or network address|ZXKitUtil.shared.getVideoSize(videoURL: URL(fileURLWithPath: path))|
|func playMusic(url: URL?, repeated: Bool = false, audioSessionCategory: AVAudioSession.Category = AVAudioSession.Category.playback)|Play music|ZXKitUtil.shared.playMusic(url: url, repeated: false)|
|func stopMusic()|Turn off music playback|ZXKitUtil.shared.stopMusic()|
|func playEffect(url: URL?, vibrate: Bool = false)|Play sound effects, silent mode will not play sound effects|ZXKitUtil.shared.playEffect(url: url, vibrate: true)|
|func startVibrate(repeated: Bool = false)|Start vibration|ZXKitUtil.shared.startVibrate()|
|func stopVibrate()|End vibration|ZXKitUtil.shared.stopVibrate()|

### File operations

|Name|Function description|Example|
|----|----|----|
|func getFileDirectory(type: ZXKitUtilFileDirectoryType)|Get folder path|ZXKitUtil.shared.getFileDirectory(type: .documents)|
|func createFileDirectory(in type: ZXKitUtilFileDirectoryType, directoryName: String)|Create a folder in the specified folder|ZXKitUtil.shared.createFileDirectory(in: .documents, directoryName: "filePath")|
|func getFileSize(filePath: URL)|Get the size of the specified file|ZXKitUtil.shared.getFileSize(filePath: url)|
|func getFileDirectorySize(fileDirectoryPth: URL)|Get the size of the specified folder|ZXKitUtil.shared.getFileDirectorySize(fileDirectoryPth: url)|

### Other

#### ZXKitUtil

|Name|Function description|Example|
|----|----|----|
|func getDictionary(object: Any, debug: Bool = false) -> [String: Any]| get all key and value from class\struct|ZXKitUtil.shared.getDictionary(object: testModel)|
|func runInMainThread(type: ZXMainThreadType = .default, function: @escaping ()->Void)|run function in main thread|ZXKitUtil.shared.runInMainThread(type: .sync) { ... }|


#### String

|Name|Function description|Example|
|----|----|----|
|func subString(rang: NSRange)|截取字符串|string.zx.subString(rang: NSRange(location: 2, length: 5))|
|func unicodeDecode()|unicode转中文|"\\u54c8\\u54c8\\u54c8".zx.unicodeDecode()|
|func unicodeEncode()|字符串转unicode|"哈哈是电话费".zx.unicodeEncode()|
|func encodeString(from originType: ZXKitUtilEncodeType = .system(.utf8), to encodeType: ZXKitUtilEncodeType)|字符串修改编码显示|"5ZOI5ZOI5piv55S16K+d6LS5".zx.encodeString(from: .base64, to: .system(.utf8))|
|func aesCBCEncrypt(password: String, ivString: String = "abcdefghijklmnop")|aes cbc Encrypt |string.zx.aesCBCEncrypt(password: "password")|
|func aesCBCDecrypt(password: String, ivString: String = "abcdefghijklmnop")|aes cbc Decrypt |string.zx.aesCBCDecrypt(password: "password")|
|func hashString(hashType: ZXKitUtilHashType, lowercase: Bool = true)|get hash value of the string|string.zx.hashString(hashType: .md5) <br/> Support md5/sha1/sha224/sha256/sha384/sha512|
|func aesGCMEncrypt(password: String, encodeType: ZXKitUtilEncodeType = .base64, nonce: AES.GCM.Nonce? = AES.GCM.Nonce())|aes gcm Encrypt |string.zx.aesGCMEncrypt(password: "password")|
|func aesGCMDecrypt(password: String, encodeType: ZXKitUtilEncodeType = .base64)|aes gcm Decrypt |string.zx.aesGCMDecrypt(password: "password")|
|func hmac(hashType: ZXKitUtilHashType, password: String, encodeType: ZXKitUtilEncodeType = .base64)|HMAC|"ZXKitUtil".zx.hmac(hashType: .sha1, password: "67FG", encodeType: .hex)|

#### Data

|Name|Function description|Example|
|----|----|----|
|static func data(from string: String, encodeType: ZXKitUtilEncodeType)|get data from string with encodeType | Data.zx.data(from: "d5a423f64b607ea7c65b311d855dc48f36114b227bd0c7a3d403f6158a9e4412", encodeType: .hex)|
|func encodeString(encodeType: ZXKitUtilEncodeType)| encode data to string with encodeType | data.zx.encodeString(encodeType: .hex)|
|func aesCBCEncrypt(password: String, ivString: String = "abcdefghijklmnop")|aes cbc Encrypt|data.zx.aesCBCEncrypt(password: "password")|
|func aesCBCDecrypt(password: String, ivString: String = "abcdefghijklmnop")|aes cbc Decrypt|data.zx.aesCBCDecrypt(password: "password")|
|func hashString(hashType: ZXKitUtilHashType, lowercase: Bool = true)|get hash value of the string|data.zx. hashString(hashType: .md5) <br/> 支持md5/sha1/sha224/sha256/sha384/sha512|
|func aesGCMEncrypt(password: String, encodeType: ZXKitUtilEncodeType = .base64, nonce: AES.GCM.Nonce? = AES.GCM.Nonce())|aes gcm Encrypt|data.zx.aesGCMEncrypt(password: "password")|
|func aesGCMDecrypt(password: String, encodeType: ZXKitUtilEncodeType = .base64)|aes gcm Decrypt|data.zx.aesGCMDecrypt(password: "password")|
|func hmac(hashType: ZXKitUtilHashType, password: String, encodeType: ZXKitUtilEncodeType = .base64)|HMAC|data.zx.hmac(hashType: .sha1, password: "67FG", encodeType: .hex)|


## License

The project is based on the MIT License