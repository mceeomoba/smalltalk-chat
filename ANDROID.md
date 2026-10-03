# Android preview build

Two independent package IDs are built from this repository, not Apex code:
- User: com.vertex.smalltalk.preview
- Admin: com.vertex.smalltalk.preview.admin

Use JDK 17, Android SDK platform/build-tools 34, Gradle 8.7 and AGP 8.3.2.
Set ANDROID_HOME or create an ignored android/local.properties with sdk.dir.
Run `python3 android-source.py`, then `cd android && gradle --no-daemon assembleUserRelease assembleAdminRelease` with Gradle 8.7 on PATH.
Release APKs are unsigned. No release key is stored in this repository.

Both flavors compile successfully. No Android runtime pass is claimed: the local
emulator stopped for insufficient RAM and this machine lacks KVM. Browser demo
screenshots do not replace Android runtime verification.

The user client intercepts https://app.local resources into bundled assets,
blocks outside navigation, disables file/content access and has no INTERNET
permission. No backend, auth, uploads, live delivery, notifications or E2EE.
The admin client is denied by default and does not enable JavaScript.
This is a local preview, not a production app or full admin implementation.
