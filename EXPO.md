# Smalltalk Expo preview

Expo user/admin source replaces the WebView Android shells. Run
`python3 expo-source.py` to materialize both standalone apps.

For each app under expo/: `npm install`, `npx expo prebuild --platform android
--no-install`. Expo 57.0.26, React Native 0.86.3, React 19.2.3, Node 22.23.3.
Icons use @expo/vector-icons Ionicons only. UI uses React Native components.
No Expo account, EAS, Expo API or access token is needed.

Generated Android project uses Gradle 9.3.1, SDK/build-tools 36, NDK
27.1.12297006, JDK 17. Ninja is required. Preview build attempt with one worker,
768MB heap and arm64-v8a reached expo-modules-core Kotlin compilation but
produced no APK in this environment. Android runtime remains unverified.
Remove release signingConfig pointing at debug before a release task.
Never commit generated keystores. Proper release key custody remains pending.

Expo web export succeeds and chat/thread/+ sheet/Games layout pixels inspected.
Calls/settings/updates/community actions are unconnected. Game card is local
same-device tic-tac-toe, NOT SENT, not turn-based multiplayer yet.
Content is placeholder only; none of the supplied contact/message screenshots
or logos/assets is in the source.

npm audit reports 23 dependency findings (16 high, 7 moderate). Review and fix
before release. No production security, E2EE or unlimited-capacity claim.
