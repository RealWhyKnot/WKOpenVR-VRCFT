# OpenVR-WKVRCFT

Fork preservation snapshot of the upstream [VRCFaceTracking](https://github.com/benaclejames/VRCFaceTracking) source (Apache-2.0). The pre-fork state is preserved on the [`archive-source`](https://github.com/RealWhyKnot/OpenVR-WKVRCFT/tree/archive-source) branch so the upstream attribution chain stays intact.

## What runs the legacy modules now

Two pieces:

1. **[OpenVR-WKPairDriver](https://github.com/RealWhyKnot/OpenVR-WKPairDriver)** -- the OpenVR-Pair umbrella. Its `modules/facetracking/` directory contains the face-tracking host sidecar (C# / .NET 10), the reflecting adapter that loads upstream `ExtTrackingModule` implementations at runtime, the SteamVR driver-side calibration / vergence-lock / eyelid-sync math, and the overlay UI.
2. **[vrcft-legacy-registry](https://github.com/RealWhyKnot/vrcft-legacy-registry)** -- the curated mirror of every module the upstream VRCFaceTracking app shows in its Modules tab. Served at `https://legacy-registry.whyknot.dev`. Auto-syncs daily; payloads are SHA-256-integrity-checked but unsigned (administrative trust).

A future native module SDK will live in the umbrella's `modules/facetracking/` tree; modules built against it ship through a separate registry. Legacy modules keep working via the compatibility shim regardless.

Each release here is the OpenVR-Pair umbrella build with `enable_facetracking.flag` pre-dropped so face and eye tracking activate immediately on install.

Issues and contributions: [OpenVR-WKPairDriver/issues](https://github.com/RealWhyKnot/OpenVR-WKPairDriver/issues).

## License

`LICENSE` on this branch is Apache-2.0, covering the preserved upstream source on `archive-source`. Release artifacts published here are the combined work from the OpenVR-Pair monorepo and ship under GPL-3.0 (see the LICENSE file inside each release zip).
