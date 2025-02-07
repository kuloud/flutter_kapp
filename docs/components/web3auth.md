# Web3Auth Flutter SDK

Web3Auth 是一个将无密码身份验证与 Web3 应用程序和钱包的非托管密钥基础设施相结合的解决方案。通过集成 OAuth（谷歌、推特、Discord）登录方式、不同的钱包以及创新的多方计算（MPC）技术，Web3Auth 为你的应用程序中的每个用户提供无缝的登录体验。

## 📖 文档

- [Web3Auth 文档](https://web3auth.io/docs)
- [SDK 参考](https://web3auth.io/docs/sdk/pnp/flutter) 

## 💡 特性

- 即插即用、基于 OAuth 的 Web3 身份验证服务
- 完全去中心化、非托管的密钥基础设施
- 端到端可白标的解决方案
- 基于阈值密码学的密钥重构
- 多因素身份验证设置与恢复（包括密码、助记词、设备因素编辑/删除等）
- 支持 WebAuthn 和无密码登录
- 支持连接多个钱包
- DApp 活跃会话管理

## ⏪ 要求

### iOS
仅支持 iOS 14 及以上版本，因为需要使用 ASWebAuthenticationSession。
- Xcode 11.4 及以上版本 / 12.x
- Swift 4.x / 5.x
- 对于 iOS 构建：`platform :ios` 需要设置为 `14.0`。请检查你的 Flutter 项目中的 `ios/Podfile` 文件进行修改。

### Android
支持 API 版本 26 或更高版本。
- 对于 Android 构建：`compileSdkVersion` 需要设置为 34。
- 请检查你的 Flutter 项目中的 `android/app/build.gradle` 文件进行修改。

## ⚡ 安装

将 `web3auth_flutter` 作为依赖项添加到你的 `pubspec.yaml` 文件中。

```yml
dependencies:
  web3auth_flutter: ^6.1.2
```

或者

```sh
flutter pub add web3auth_flutter
```

## 🌟 配置

查阅 [SDK 参考](https://web3auth.io/docs/sdk/pnp/flutter/install) 以配置 Android 和 iOS 构建。

## 🩹 示例

在我们的 [示例](https://web3auth.io/docs/examples) 中查看你首选的区块链和平台的示例。

```dart
// 初始化
await Web3AuthFlutter.init(
  Web3AuthOptions(
    // 从 dashboard.web3auth.io 获取你的客户端 ID
    clientId: 'YOUR_WEB3AUTH_CLIENT_ID',
    network: Network.sapphire_devnet,
    // 你的重定向 URL，请查看如何配置。
    // 安卓：https://web3auth.io/docs/sdk/pnp/flutter/install#android-configuration
    // iOS：https://web3auth.io/docs/sdk/pnp/flutter/install#ios-configuration
    redirectUrl: redirectUrl,
  ),
);

// 调用 initialize() 函数以在用户有活跃会话时获取私钥和用户信息而无需重新登录
// 如果没有活跃会话，该函数将抛出错误。
await Web3AuthFlutter.initialize();

// 登录
await Web3AuthFlutter.login(LoginParams(loginProvider: Provider.google));

// 登出
await Web3AuthFlutter.logout();
```

## 在安卓上触发用户取消操作

在安卓系统中，如果你想在用户关闭浏览器标签时触发异常，你必须在登录屏幕中使用 `WidgetsBindingObserver` 混入。

```dart
class LoginScreen extends State<MyApp> with WidgetsBindingObserver {
 
  @override
  void initState() {
    super.initState();
    WidgetsBinding.instance.addObserver(this);
  }
  @override
  void dispose() {
    super.dispose();
    WidgetsBinding.instance.removeObserver(this);
  }
  @override
  void didChangeAppLifecycleState(final AppLifecycleState state) {
    // 这对于在安卓上触发用户取消操作很重要。
    if (state == AppLifecycleState.resumed) {
      Web3AuthFlutter.setCustomTabsClosed();
    }
  }
  
   @override
  Widget build(BuildContext context) { 
    // 你的 UI 代码
  }
  Future<void> _login() async {
    try {
      await Web3AuthFlutter.login(LoginParams(loginProvider: Provider.google));
    } on UserCancelledException {
        log("用户取消操作。");
    } on UnKnownException {
        log("发生未知异常");
    } catch (e) {
        log(e.toString());
    }
  }
}
```

## 🌐 演示

查看 [Web3Auth 演示](https://demo-app.web3auth.io/)，了解如何在应用程序中使用 Web3Auth。

查看我们的 [Web3Auth 即插即用 Flutter 快速入门](https://web3auth.io/docs/quick-start?product=PNP&sdk=PNP_FLUTTER&framework=IOS&stepIndex=0)，帮助你在 Flutter 应用程序中快速集成 Web3Auth 即插即用的基本实例。

进一步查看此仓库中的 [示例文件夹](https://github.com/Web3Auth/web3auth-flutter-sdk/tree/master/example)，其中包含一个示例应用程序。

## 💬 故障排除与支持

- [社区门户](https://community.web3auth.io/)
- [故障排除文档页面](https://web3auth.io/docs/troubleshooting) 