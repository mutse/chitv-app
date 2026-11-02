# ChiTV releases

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

## English

Android tags are built from `mutse/chitv-app-android` and published as APKs in this repository's GitHub Releases.

### Setup

1. In `mutse/chitv-app-android`, add the Actions secret `CHITV_RELEASE_DISPATCH_TOKEN`: a fine-grained personal access token with access to `mutse/chitv-app` and **Contents: read and write** permission, allowing the workflow to publish releases in this repository.
2. Push a new tag to `mutse/chitv-app-android`. Its workflow builds that exact commit and publishes `app-release.apk` under the same tag as a Release in this repository. GitHub creates the corresponding tag in this repository if it does not exist.

Check the Android repository's Actions runs if a release fails. The Android project's current release configuration uses a debug signing key, so these APKs do not have a stable production signing identity.
