# Pocketforge toolchain bundles

The build tools **Pocketforge by Aninda Studio** downloads to a phone at first run. This repository holds only release assets; the app's source lives in a separate repository.

Each release is one toolchain channel named by date (for example `toolchain-2026.10.30`). The app's `manifest.json` names the channel, the file names and the SHA-256 checksums; the installer refuses any file whose checksum differs.

| File | What it is | Licence |
|---|---|---|
| `runtime-jdk17-arm64-<version>.tar.gz` | OpenJDK 17 for arm64 Android, repackaged unmodified from the Termux `openjdk-17` package together with the shared libraries it links against (libandroid-shmem, libandroid-spawn, libiconv, zlib, libc++, libandroid-support) | GPL v2 with the Classpath Exception; the licence files are inside under `jdk17/legal/` |
| `runtime-aapt2libs-arm64-<version>.tar.gz` | The shared libraries the Termux build of `aapt2` links against (abseil-cpp, protobuf, fmt, libc++, expat, libpng, zopfli, zlib) | Each library's own licence (Apache-2.0, BSD-3, MIT, zlib) |

Nothing from Google's Android SDK is in these bundles. The Android platform and build tools are downloaded from Google by the person using the app, after they accept Google's licence inside the app.

The bundles are produced by `tools/termux-bundle.py` in the Pocketforge repository from the Termux package repository (aarch64, stable). Termux packages are rebuilt from upstream source by the Termux project; nothing here is modified.
