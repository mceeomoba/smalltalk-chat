name: Android preview
on:
  workflow_dispatch:
permissions:
  contents: read
jobs:
  preview:
    runs-on: ubuntu-latest
    timeout-minutes: 30
    strategy:
      matrix:
        client: [user, admin]
      fail-fast: false
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '22'
      - uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'
      - uses: android-actions/setup-android@v3
      - name: Materialize audited independent source and dependency locks
        run: |
          python3 expo-source.py
          python3 expo-locks.py
      - name: Install dependencies
        working-directory: expo/${{ matrix.client }}
        run: npm ci --no-audit --no-fund
      - name: Local Expo prebuild (no account or token)
        working-directory: expo/${{ matrix.client }}
        env:
          CI: '1'
        run: npx expo prebuild --platform android --no-install
      - name: Install native toolchain
        run: sdkmanager 'platforms;android-36' 'build-tools;36.0.0' 'ndk;27.1.12297006' 'cmake;3.22.1'
      - name: Preview APK (generated debug signature, not production)
        working-directory: expo/${{ matrix.client }}/android
        run: |
          chmod +x gradlew
          ./gradlew --no-daemon --max-workers 2 -PreactNativeArchitectures=arm64-v8a assembleRelease
      - name: Upload preview only
        uses: actions/upload-artifact@v4
        with:
          name: smalltalk-${{ matrix.client }}-preview-debug-signed
          path: expo/${{ matrix.client }}/android/app/build/outputs/apk/release/*.apk
          retention-days: 1
          if-no-files-found: error
