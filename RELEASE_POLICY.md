# Android 发布制品规则

该仓库是 `Codex汉化增强版` 移动端的公开制品仓库，不是源码仓库。

## 每个正式版本允许的文件

- `codex-mobile-v<version>-android.apk`
- `codex-mobile-v<version>-android-ota.zip`
- `codex-mobile-v<version>-android-ota-manifest.json`
- `SHA256SUMS.txt`

OTA ZIP 内只允许：

- 编译后的 Android Hermes `.hbc` 字节码
- 运行时图片和字体
- 脱敏后的 Android OTA 清单
- 包内 SHA-256 校验和

## 禁止发布

- JavaScript、TypeScript、Java、Kotlin、C/C++、Swift 等源码
- source map、源码归档、Git 工作树或 Git 元数据
- `node_modules`、包管理清单与锁文件、Gradle 工程文件
- `.env`、Secrets、API Token、证书、私钥、keystore、签名配置
- 调试签名、未签名或签名校验失败的 APK

发布脚本会检查精确文件白名单、压缩包内部路径、源码/敏感文件扩展名、APK 签名、版本、Git 提交状态和 SHA-256。任何一项失败都会停止发布，已有版本标签不得覆盖。

