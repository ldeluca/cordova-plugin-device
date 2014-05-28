<!---
    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.
-->

# org.apache.cordova.device

这个插件定义全球 `device` 对象，描述该设备的硬件和软件。 虽然对象是在全球范围内，但不是可用，直到后 `deviceready` 事件。

    document.addEventListener("deviceready", onDeviceReady, false);
    function onDeviceReady() {
        console.log(device.cordova);
    }
    

## 安装

    cordova plugin add org.apache.cordova.device
    

## 属性

*   device.cordova
*   device.model
*   device.name
*   device.platform
*   device.uuid
*   device.version

## device.cordova

获取Cordova在设备上运行的版本。

### 支持的平台

*   亚马逊火 OS
*   Android 系统
*   黑莓 10
*   火狐浏览器操作系统
*   iOS
*   Tizen
*   Windows Phone 7 和 8
*   Windows 8

## device.model

`device.model`返回设备的模型或产品的名称。值由设备制造商设置，并且同一产品的不同版本可能不同。

### 支持的平台

*   Android 系统
*   黑莓 10
*   iOS
*   Tizen
*   Windows Phone 7 和 8
*   Windows 8

### 快速的示例

    / / Android： Nexus 返回"激情"（Nexus One 代码名称） / / 摩托罗拉 Droid 返回"田鼠"/ / 黑莓手机： 火炬 9800 返回"9800"/ / iOS： 迷你 ipad，返回与 iPad2，5 ；iPhone 5 是 iPhone 5，1。 请参阅 http://theiphonewiki.com/wiki/index.php?title=Models / / var 模型 = device.model ；
    

### Android 的怪癖

*   获取[product name][1]来代替[model name][2]，这往往是生产代码名称。 例如，Nexus One 返回 `Passion` ，并且Motorola Droid 返回`voles`.

 [1]: http://developer.android.com/reference/android/os/Build.html#PRODUCT
 [2]: http://developer.android.com/reference/android/os/Build.html#MODEL

### Tizen 怪癖

*   返回与供应商指派的设备型号，例如，`TIZEN`

### Windows Phone 7 和 8 怪癖

*   返回由制造商指定的设备型号。例如，Samsung Focus返回`SGH-i917`.

## device.name

**WARNING**： `device.name` 从2.3.0版本中 已被否决。使用 `device.model` 替代。

## device.platform

获取该设备的操作系统名称。

    var string = device.platform;
    

### 支持的平台

*   Android 系统
*   黑莓 10
*   火狐浏览器操作系统
*   iOS
*   Tizen
*   Windows Phone 7 和 8
*   Windows 8

### 快速的示例

    // Depending on the device, a few examples are:
    //   - "Android"
    //   - "BlackBerry 10"
    //   - "iOS"
    //   - "WinCE"
    //   - "Tizen"
    var devicePlatform = device.platform;
    

### Windows Phone 7 的怪癖

Windows Phone 7 作为`WinCE`设备报告给平台.

### Windows Phone 8 怪异

Windows Phone 8 作为`Win32NT`设备报告给平台.

## device.uuid

获取设备的通用唯一标识符 ([UUID][3]).

 [3]: http://en.wikipedia.org/wiki/Universally_Unique_Identifier

    var string = device.uuid;
    

### 说明

UUID 如何生成的详细信息由设备制造商和特定于设备的平台或型号。

### 支持的平台

*   Android 系统
*   黑莓 10
*   iOS
*   Tizen
*   Windows Phone 7 和 8
*   Windows 8

### 快速的示例

    / / Android： 返回一个随机的 64 位整数 （再次作为字符串返回!)
    / / 设备的第一次启动生成的整数
    / / 
    / / BlackBerry： 返回设备的 PIN 号码 
    / / 这是九个数字的唯一整数 （作为字符串，虽然!) 
    / / 
    / / iPhone： （从 UIDevice 类文档解释） 
    / / 从创建的多个硬件标识中返回一个字符串的哈希值。
    / / 它保证每个设备的唯一性，并不能绑定 
    / / 到用户帐户。
    / / Windows Phone 7： 返回的哈希代码的设备 + 当前用户，
    / / 如果是未定义用户，则一个 guid 生成并且将会持续到该应用程序被卸载 
    / / Tizen： 返回设备的 IMEI (国际移动设备身份或 IMEI 是一个数字 
    / / 独有的每一个 UMTS 和 GSM 移动电话。
    var deviceID = device.uuid;
    

### iOS 的怪异

`uuid`在 iOS 上不是独有的一种设备，但对于每个应用程序，每个安装各不相同。 如果你删除并重新安装应用程序，也可能在你升级iOS的时候，甚至每升级版本的应用程序（在IOS5.1明显）的变化。 `uuid`不是一个可靠的值。

### Windows Phone 7 和 8 怪癖

`uuid`为 Windows Phone 7 需要权限 `ID_CAP_IDENTITY_DEVICE` 。 Microsoft 可能会很快就弃用此属性。 如果能力不是可用的，应用程序将生成一个持久性的 guid 并保持应用程序的安装在设备上的持续时间。

## device.version

获取操作系统版本。

    var string = device.version;
    

### 支持的平台

*   Android 2.1 +
*   黑莓 10
*   iOS
*   Tizen
*   Windows Phone 7 和 8
*   Windows 8

### 快速的示例

    / / Android： Froyo OS 将返回"2.2"
    / / Eclair OS 将返回"2.1"、"2.0.1"2.0"
    / / 版本也可以返回更新级别"2.1 update1"
    / / 
    / / BlackBerry： Torch 9800 使用 OS 6.0 将返回"6.0.0.600"
    / / 
    / / iPhone： iOS 3.2 返回"3.2"
    / / 
    / / Windows Phone 7： 返回当前 OS 版本号。 on Mango returns 7.10.7720
    // Tizen: returns "TIZEN_20120425_2"
    var deviceVersion = device.version;