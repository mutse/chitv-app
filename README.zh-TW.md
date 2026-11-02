# ChiTV 發布

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

當 `mutse/chitv-app-android` 推送標籤時，自動建置 Android APK，並發布至本儲存庫的 GitHub Releases。

## 設定步驟

1. 在 `mutse/chitv-app-android` 中新增 Actions secret `CHITV_RELEASE_DISPATCH_TOKEN`：使用可存取 `mutse/chitv-app` 且具有 **Contents: read and write** 權限的細緻權限個人存取權杖，允許工作流程在本儲存庫發布 Release。
2. 向 `mutse/chitv-app-android` 推送新標籤。其工作流程會建置該確切提交，並以相同標籤在本儲存庫發布 `app-release.apk`。如果本儲存庫尚無對應標籤，GitHub 會建立該標籤。

如果發布失敗，請檢查 Android 儲存庫的 Actions 執行紀錄。Android 專案目前的 release 設定使用偵錯簽署金鑰，因此產生的 APK 沒有穩定的正式簽署身分。
