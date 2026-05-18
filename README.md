# WKOpenVR-VRCFT

Face and eye tracking on SteamVR, packaged as a one-feature install of the WKOpenVR umbrella. Builds on the upstream VRCFaceTracking codebase for vendor module loading and the Unified Expressions parameter shape, then routes the data through a C# .NET 10 sidecar into the WKOpenVR driver and out to VRChat over OSC.

## What this is for

You have a face-tracked HMD -- a Quest Pro, an Aero with the eye-tracking module, a Vive Pro Eye, a Beyond, a PSVR2 hooked up over the PC bridge, anything that produces Unified Expressions -- and you want it to actually drive your avatar. The upstream VRCFaceTracking app does that, but it runs as a standalone tray app you have to keep alive, exposes OSC to one avatar pattern at a time, and doesn't talk to the rest of your SteamVR stack.

What this gives you:

- **Pre-enabled face and eye tracking** on install. The driver-side integration comes up live the first time SteamVR starts. Pick a vendor module from the in-overlay Modules tab and parameters start flowing.
- **Upstream VRCFT vendor module compatibility** via a reflecting adapter. Existing third-party modules (Virtual Desktop's, the various Quest Pro modules, custom community builds) load as-is.
- **Curated legacy module registry** at [legacy-registry.whyknot.dev](https://legacy-registry.whyknot.dev) -- mirror of every module the upstream Modules tab shows, auto-synced daily, SHA-256-integrity-checked, so the in-overlay registry actually finds modules to download.
- **Driver-side eyelid sync, vergence lock, and continuous calibration** of the eye-tracking signal. The cleaned values feed every consumer rather than being applied per-app.
- **Dual-emit OSC paths** per frame: legacy bare-name (`/avatar/parameters/JawOpen`) and modern v2 (`/avatar/parameters/v2/JawOpen`). Stock VRCFT avatars built against either convention pick up data.
- **Unified Expressions v5.1.1.0** aligned with current upstream, with semantic aliases for upstream's recent rename pass (MouthClose, Smile, Sad, etc.).

## Status

Face tracking is in active development inside the umbrella. Releases will be mirrored here from the WKOpenVR umbrella when the module is ready for general distribution. Build from source via [WKOpenVR](https://github.com/RealWhyKnot/WKOpenVR) in the meantime.

## Source

Source lives in [WKOpenVR](https://github.com/RealWhyKnot/WKOpenVR), the umbrella repository for the WKOpenVR feature modules. This repo is a release mirror.

## Upstream

The C# host sidecar, the reflection bridge that loads upstream `ExtTrackingModule` implementations, and the legacy module registry are derived from [benaclejames/VRCFaceTracking](https://github.com/benaclejames/VRCFaceTracking) by Benjamin Clarke and contributors (Apache-2.0). The [`archive-source`](https://github.com/RealWhyKnot/WKOpenVR-VRCFT/tree/archive-source) branch preserves the upstream tree as it stood when this fork seeded, so the attribution chain stays intact.

The driver-side integration (calibration, eyelid sync, vergence lock), the shared-memory ring protocol between the host and the driver, the OSC publisher, and the overlay UI are new in [WKOpenVR](https://github.com/RealWhyKnot/WKOpenVR).

## Issues and contributions

Open them at [WKOpenVR/issues](https://github.com/RealWhyKnot/WKOpenVR/issues).

## License

`LICENSE` on this branch is Apache-2.0, covering the preserved upstream source on `archive-source`. Combined work in the WKOpenVR umbrella ships under GPL-3.0; the LICENSE file inside each release zip reflects the umbrella's terms.
