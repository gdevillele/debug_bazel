# debug_bazel

**Context**

I am trying to build a C++ library (libpng) using Bazel **8.1.0**.

## Build commands

### wasm

```bash
bazel build //deps/lpng/src:png --platforms=//:wasm_wasm32
bazel build //deps/lpng/src:png --platforms=//:wasm_wasm64
```

### Windows

```bash
bazel build //deps/lpng/src:png --platforms=//:windows_x86_64
```

### macOS

Commands that works:

```bash
bazel build //deps/lpng/src:png --platforms=//:macos_arm64
bazel build //deps/lpng/src:png --platforms=//:macos_x86_64
```
