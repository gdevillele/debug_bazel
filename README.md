# debug_bazel

**Context**

I am trying to build a C++ library (libpng) using Bazel **8.0.1** on a 2021 Macbook Pro M1.

**Environment variables**

```bash
export ANDROID_HOME=~/Library/Android/sdk
export ANDROID_NDK_HOME=~/Library/Android/sdk/ndk/27.2.12479018
```

## Build commands

### Android

```bash
bazel build //deps/lpng/src:png --platforms=//:android_armv7
bazel build //deps/lpng/src:png --platforms=//:android_arm64
bazel build //deps/lpng/src:png --platforms=//:android_x86_32
bazel build //deps/lpng/src:png --platforms=//:android_x86_64
```

### macOS

Commands that works:

```bash
bazel build //deps/lpng/src:png --platforms=//:macos_universal
```
