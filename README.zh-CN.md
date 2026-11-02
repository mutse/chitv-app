# ChiTV 发布

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

当 `mutse/chitv-app-android` 推送标签时，自动构建 Android APK，并发布到本仓库的 GitHub Releases。

## 配置步骤

1. 在 `mutse/chitv-app-android` 中添加 Actions secret `CHITV_RELEASE_DISPATCH_TOKEN`：使用可访问 `mutse/chitv-app` 且具有 **Contents: read and write** 权限的细粒度个人访问令牌，允许工作流在本仓库发布 Release。
2. 向 `mutse/chitv-app-android` 推送新标签。其工作流会构建该确切提交，并以相同标签在本仓库发布 `app-release.apk`。如果本仓库尚无对应标签，GitHub 会创建该标签。

如果发布失败，请检查 Android 仓库的 Actions 运行记录。Android 项目当前的 release 配置使用调试签名密钥，因此生成的 APK 没有稳定的正式签名身份。
