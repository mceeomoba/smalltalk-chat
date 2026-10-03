# Smalltalk chat - Vertex draft

Independent user/admin Android chat app in phased development. Current UI is
local-demo text chat and same-device tic-tac-toe, not a live service.
Backend identity/auth and storage remain pending. No E2EE or unlimited claims.

Run `node --test core.test.mjs`. Serve repository root over HTTP for web preview.
Run `python3 android-source.py` to materialize Android source. See ANDROID.md
for JDK/SDK/Gradle requirements and unsigned release build commands.

Both Android flavors compile. Android runtime verification and signing remain
blocked; unsigned outputs are not release-ready. No wallet/financial keys,
spend or Apex code. See PLAN.md for remaining phases and gates.
