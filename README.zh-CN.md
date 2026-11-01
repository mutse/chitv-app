# ChiTV 发布

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

当 `mutse/chitv-app-android` 推送标签时，自动构建 Android APK，并发布到本仓库的 GitHub Releases。

## 配置步骤

1. 将 `.github/workflows/android-release.yml` 提交并推送到 `mutse/chitv-app` 的默认分支。
2. 将 `integration/chitv-app-android/.github/workflows/notify-chitv-release.yml` 复制到 `mutse/chitv-app-android` 的 `.github/workflows/notify-chitv-release.yml`，提交并推送到该仓库的默认分支。创建标签所指向的提交也必须包含此工作流。
3. 在 `mutse/chitv-app-android` 中添加 Actions secret `CHITV_RELEASE_DISPATCH_TOKEN`：使用可访问 `mutse/chitv-app` 且具有 **Contents: read and write** 权限的细粒度个人访问令牌或 GitHub App 安装令牌，以发送仓库分发事件。
4. 在 `mutse/chitv-app` 中添加 Actions secret `ANDROID_SOURCE_TOKEN`：使用可访问 `mutse/chitv-app-android` 且具有 **Contents: read** 权限的令牌。如果 Android 仓库是公开的，也可以修改工作流中的检出令牌，改用默认的 `GITHUB_TOKEN`。
5. 向 `mutse/chitv-app-android` 推送新标签。其工作流会发送标签和提交 SHA；本仓库会构建该确切提交，并以相同标签发布 `app-release.apk`。如果本仓库尚无对应标签，GitHub 会创建该标签。

如果发布失败，请检查两个仓库的 Actions 运行记录。Android 项目当前的 release 配置使用调试签名密钥，因此生成的 APK 没有稳定的正式签名身份。
