# ChiTV 發布

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

當 `mutse/chitv-app-android` 推送標籤時，自動建置 Android APK，並發布至本儲存庫的 GitHub Releases。

## 設定步驟

1. 將 `.github/workflows/android-release.yml` 提交並推送至 `mutse/chitv-app` 的預設分支。
2. 將 `integration/chitv-app-android/.github/workflows/notify-chitv-release.yml` 複製到 `mutse/chitv-app-android` 的 `.github/workflows/notify-chitv-release.yml`，提交並推送至該儲存庫的預設分支。建立標籤所指向的提交也必須包含此工作流程。
3. 在 `mutse/chitv-app-android` 中新增 Actions secret `CHITV_RELEASE_DISPATCH_TOKEN`：使用可存取 `mutse/chitv-app` 且具有 **Contents: read and write** 權限的細緻權限個人存取權杖或 GitHub App 安裝權杖，以傳送儲存庫分發事件。
4. 在 `mutse/chitv-app` 中新增 Actions secret `ANDROID_SOURCE_TOKEN`：使用可存取 `mutse/chitv-app-android` 且具有 **Contents: read** 權限的權杖。如果 Android 儲存庫是公開的，也可以修改工作流程中的檢出權杖，改用預設的 `GITHUB_TOKEN`。
5. 向 `mutse/chitv-app-android` 推送新標籤。其工作流程會傳送標籤與提交 SHA；本儲存庫會建置該確切提交，並以相同標籤發布 `app-release.apk`。如果本儲存庫尚無對應標籤，GitHub 會建立該標籤。

如果發布失敗，請檢查兩個儲存庫的 Actions 執行紀錄。Android 專案目前的 release 設定使用偵錯簽署金鑰，因此產生的 APK 沒有穩定的正式簽署身分。
