# OpenVR-WKVRCFT

Release mirror for the FaceTracking module of the [OpenVR-Pair](https://github.com/RealWhyKnot/OpenVR-WKPairDriver) umbrella toolset. Each release here is the OpenVR-Pair umbrella build with `enable_facetracking.flag` pre-dropped so face and eye tracking activate immediately on install.

This repository is also a fork preservation snapshot. The original source it was forked from is at https://github.com/benaclejames/VRCFaceTracking. Pre-fork state is preserved on the [`archive-source`](https://github.com/RealWhyKnot/OpenVR-WKVRCFT/tree/archive-source) branch so the Apache-2.0 attribution chain stays intact.

Active development of the FaceTracking module -- the C# .NET 10 host sidecar plus the driver-side continuous calibration, skew-line vergence lock, and confidence-weighted eyelid sync -- lives at [modules/facetracking/](https://github.com/RealWhyKnot/OpenVR-WKPairDriver/tree/main/modules/facetracking) in the umbrella repo.

Issues and contributions: open them at [OpenVR-WKPairDriver/issues](https://github.com/RealWhyKnot/OpenVR-WKPairDriver/issues).

## License

`LICENSE` on this branch is Apache-2.0, covering the preserved upstream source on `archive-source`. Release artifacts published here are the combined work from the OpenVR-Pair monorepo and ship under GPL-3.0 (see the LICENSE file inside each release zip).
