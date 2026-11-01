# ChiTV releases

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

## English

Android tags are built from `mutse/chitv-app-android` and published as APKs in this repository's GitHub Releases.

### Setup

1. Commit and push `.github/workflows/android-release.yml` to the default branch of `mutse/chitv-app`.
2. Copy `integration/chitv-app-android/.github/workflows/notify-chitv-release.yml` to `.github/workflows/notify-chitv-release.yml` on the default branch of `mutse/chitv-app-android`, then commit and push it. The workflow must also be present in the commit being tagged.
3. In `mutse/chitv-app-android`, add the Actions secret `CHITV_RELEASE_DISPATCH_TOKEN`: a fine-grained personal access token or GitHub App installation token with access to `mutse/chitv-app` and **Contents: read and write** permission, allowing repository dispatch.
4. In `mutse/chitv-app`, add the Actions secret `ANDROID_SOURCE_TOKEN`: a token with access to `mutse/chitv-app-android` and **Contents: read** permission. For a public Android repository, the default `GITHUB_TOKEN` can be used instead by changing the checkout token in the workflow.
5. Push a new tag to `mutse/chitv-app-android`. Its workflow dispatches the tag and commit SHA; the release repository builds that exact commit and publishes `app-release.apk` under the same tag. GitHub creates the corresponding tag in this repository if it does not exist.

Check both repositories' Actions runs if a release fails. The Android project's current release configuration uses a debug signing key, so these APKs do not have a stable production signing identity.
