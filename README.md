Test Device Policy Control (Test DPC) App
=========================================

基于[android-testdcp](https://github.com/googlesamples/android-testdpc)构建方式更改为gradle, 并进行汉化.

入门指南
---------------
- 原项目使用 Bazel 构建系统, 先项目改为 Gradle 构建系统。
- 构建命令：`./gradlew build -x test -x lint`

配置方法
------------

You can find various kinds of provisioning methods [here](https://developers.google.com/android/work/prov-devices#Key_provisioning_differences_across_android_releases). Let's take a few of them as an example.

#### QR code provisioing (Device Owner N+ only) ####
1. Factory reset your device and tap the welcome screen in setup wizard 6 times.
2. The setup wizard prompts the user to connect to the Internet so the setup wizard can download a QR code reader.
3. Modify (if needed) and scan [this QR code] (http://down-box.appspot.com/qr/nQB0tw7b).
4. Follow onscreen instructions

#### ADB command ####

**Device Owner**

*   Run the `adb` command:

    ```console
    adb shell dpm set-device-owner com.afwsamples.testdpc/.DeviceAdminReceiver
    ```

**Profile Owner**

*   Create a managed profile by launching the “Set up TestDPC” app (if this app
    seems broken and you are in dark mode, switch to light mode)
*   Skip adding an account at the end of the flow

**COPE Profile Owner**

*   Create a managed profile by launching the “Set up TestDPC” app (if this app
    seems broken and you are in dark mode, switch to light mode)
*   Skip adding an account at the end of the flow
*   Run the `adb` command:

    ```console
    adb shell dpm mark-profile-owner-on-organization-owned-device --user 10 com.afwsamples.testdpc/.DeviceAdminReceiver`
    ```

## TestDPC as DM role holder

TestDPC v9.0.5+ can be setup as Device Management Role Holder.

*   Running the following `adb` commands:

    ```console
    adb shell cmd role set-bypassing-role-qualification true
    adb shell cmd role add-role-holder android.app.role.DEVICE_POLICY_MANAGEMENT com.afwsamples.testdpc
    ```

    Note: unlike DO/PO, this change is not persisted so TestDPC needs to be
    marked as role holder again if the device reboots.

Support
-------

If you've found an error in this sample, please file an issue:
https://github.com/googlesamples/android-testdpc/issues

Patches are encouraged, and may be submitted by forking this project and submitting a pull request through GitHub.

License
-------

Licensed under the Apache 2.0 license. See the LICENSE file for details.

How to make contributions?
--------------------------

Please read and follow the steps in the CONTRIB file.
