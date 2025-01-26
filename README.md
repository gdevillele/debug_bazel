# debug_bazel

**Context**

I am trying to build a C++ library for Android using Bazel **8.0.1** on a 2021 Macbook Pro M1.

**Environment variables**

```bash
export ANDROID_HOME=~/Library/Android/sdk
export ANDROID_NDK_HOME=~/Library/Android/sdk/ndk/27.2.12479018
```

## Build commands (not working)

```bash
bazel build //deps/lpng/src:png --platforms=//:android_armv7
bazel build //deps/lpng/src:png --platforms=//:android_arm64
bazel build //deps/lpng/src:png --platforms=//:android_x86_32
bazel build //deps/lpng/src:png --platforms=//:android_x86_64
```

**Error logs**

```
% bazel build //deps/lpng/src:png --platforms=//:android_arm64
ERROR: Traceback (most recent call last):
	File "/private/var/tmp/_bazel_gaetan/40aa809e6cb956d16fc419bcc6ec9eca/external/rules_android_ndk++android_ndk_repository_extension+androidndk/toolchains/llvm/prebuilt/darwin-x86_64/BUILD.bazel", line 48, column 16, in <toplevel>
		srcs = glob([
Error in glob: glob pattern 'lib64/**/*' didn't match anything, but allow_empty is set to False (the default value of allow_empty can be set with --incompatible_disallow_empty_glob).
ERROR: /Users/gaetan/projects/gdevillele/debug_bazel/deps/lpng/src/BUILD:3:11: Target '//deps/lpng/src:png' depends on toolchain '@@rules_android_ndk++android_ndk_repository_extension+androidndk//toolchains/llvm/prebuilt/darwin-x86_64:cc_toolchain_aarch64-linux-android', which cannot be found: Target '@@rules_android_ndk++android_ndk_repository_extension+androidndk//toolchains/llvm/prebuilt/darwin-x86_64:cc_toolchain_aarch64-linux-android' contains an error and its package is in error'
ERROR: Analysis of target '//deps/lpng/src:png' failed; build aborted: Analysis failed
INFO: Elapsed time: 0.184s, Critical Path: 0.00s
INFO: 1 process: 1 internal.
ERROR: Build did NOT complete successfully
```

## Build commands (working)

I am using Bazel 8.0.1, and I have to use the `--incompatible_disallow_empty_glob=false` flag, otherwise I get the error.
From what I have read, this is due to Bazel 8.0 having "allow_empty" set to false by default for `glob()`.

```bash
bazel build //deps/lpng/src:png --platforms=//:android_armv7 --incompatible_disallow_empty_glob=false
bazel build //deps/lpng/src:png --platforms=//:android_arm64 --incompatible_disallow_empty_glob=false
bazel build //deps/lpng/src:png --platforms=//:android_x86_32 --incompatible_disallow_empty_glob=false
bazel build //deps/lpng/src:png --platforms=//:android_x86_64 --incompatible_disallow_empty_glob=false
```
