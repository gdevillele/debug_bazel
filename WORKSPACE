load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "emsdk",
    integrity = "sha256-Tocufv3hs3heo+sK1H01kVii5yu/+WsS+/ph5r1mKqg=",
    strip_prefix = "emsdk-4.0.1/bazel",
    urls = ["https://github.com/emscripten-core/emsdk/archive/refs/tags/4.0.1.tar.gz"],
)

load("@emsdk//:deps.bzl", emsdk_deps = "deps")

emsdk_deps()

load("@emsdk//:emscripten_deps.bzl", emsdk_emscripten_deps = "emscripten_deps")

emsdk_emscripten_deps()

load("@emsdk//:toolchains.bzl", "register_emscripten_toolchains")

register_emscripten_toolchains()
