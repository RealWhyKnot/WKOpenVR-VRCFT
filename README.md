# WKOpenVR-VRCFT

Fork preservation snapshot of the upstream [VRCFaceTracking](https://github.com/benaclejames/VRCFaceTracking) source (Apache-2.0). The pre-fork state is preserved on the [`archive-source`](https://github.com/RealWhyKnot/WKOpenVR-VRCFT/tree/archive-source) branch so the upstream attribution chain stays intact.

## What runs the legacy modules now

Two pieces:

1. **[WKOpenVR](https://github.com/RealWhyKnot/WKOpenVR)** -- the WKOpenVR umbrella. Its `modules/facetracking/` directory contains the face-tracking host sidecar (C# / .NET 10), the reflecting adapter that loads upstream `ExtTrackingModule` implementations at runtime, the SteamVR driver-side calibration / vergence-lock / eyelid-sync math, and the overlay UI.
2. **[wkvrcft-legacy-registry](https://github.com/RealWhyKnot/wkvrcft-legacy-registry)** -- the curated mirror of every module the upstream VRCFaceTracking app shows in its Modules tab. Served at `https://legacy-registry.whyknot.dev`. Auto-syncs daily; payloads are SHA-256-integrity-checked but unsigned (administrative trust).

A future native module SDK will live in the umbrella's `modules/facetracking/` tree; modules built against it ship through a separate registry. Legacy modules keep working via the compatibility shim regardless.

Each release here ships both a `WKOpenVR-FaceTracking-<version>.zip` (the WKOpenVR umbrella build with `enable_facetracking.flag` pre-dropped so face and eye tracking activate immediately on install) and a `WKOpenVR-FaceTracking-v<version>-Setup.exe` (NSIS installer that does the same plus a Start Menu shortcut and an uninstaller).

## Issues and contributions

[WKOpenVR/issues](https://github.com/RealWhyKnot/WKOpenVR/issues).

## License

`LICENSE` on this branch is Apache-2.0, covering the preserved upstream source on `archive-source`. Release artifacts published here are the combined work from the WKOpenVR monorepo and ship under GPL-3.0 (see the LICENSE file inside each release zip).
