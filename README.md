### Test Device Policy Control (Test DPC) App

#### 简介
Test DPC 是一个应用程序，旨在帮助 EMM、ISV 和 OEM 测试其应用程序和平台在 Android 企业托管配置文件（即工作配置文件）中的表现。它既是一个示例设备策略控制器，也是一个测试应用程序，用于测试 Android 企业可用的 API。支持运行 Android 5.0 Lollipop 或更高版本的设备。

更多关于 Android 企业应用的信息，请参阅[官方文档](https://developer.android.com/work/index.html)。

#### 入门指南
- 原项目使用 Bazel 构建系统, 先项目改为 Gradle 构建系统。
- 构建命令：`./gradlew build -x test -x lint`

#### 配置方法
提供了几种不同的配置方法，例如：
- **QR 码配置（仅限设备所有者 N+）**：通过扫描 QR 码完成配置。
- **ADB 命令**：
    - **设备所有者**：`adb shell dpm set-device-owner com.afwsamples.testdpc/.DeviceAdminReceiver`
    - **配置文件所有者**：通过启动“设置 TestDPC”应用创建托管配置文件。
    - **COPE 配置文件所有者**：结合 ADB 命令创建托管配置文件。

#### TestDPC 作为设备管理角色持有者
从 v9.0.5 版本开始，TestDPC 可以设置为设备管理角色持有者。需要执行以下 ADB 命令：
```console
adb shell cmd role set-bypassing-role-qualification true
adb shell cmd role add-role-holder android.app.role.DEVICE_POLICY_MANAGEMENT com.afwsamples.testdpc
```

#### 支持与贡献
- 如果发现错误，请提交问题：[GitHub Issues](https://github.com/googlesamples/android-testdpc/issues)
- 欢迎提交补丁，可以通过 fork 项目并提交 pull request 来贡献代码。

#### 许可证
- 本项目采用 Apache 2.0 许可证。详情请参阅 LICENSE 文件。

#### 如何贡献
- 请阅读并遵循 CONTRIB 文件中的步骤。

以上是 README.md 文件的主要内容概述。如果你有更具体的问题或需要进一步的帮助，请告诉我！