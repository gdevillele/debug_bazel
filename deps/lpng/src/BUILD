load("@rules_cc//cc:defs.bzl", "cc_library")
# load("@emsdk//emscripten_toolchain:wasm_rules.bzl", "wasm_cc_binary")

cc_library(
    name = "png",
    srcs = [
        "png.c",
        "pngdebug.h",
        "pngerror.c",
        "pngget.c",
        "pnginfo.h",
        "pnglibconf.h",
        "pngmem.c",
        "pngpread.c",
        "pngpriv.h",
        "pngread.c",
        "pngrio.c",
        "pngrtran.c",
        "pngrutil.c",
        "pngset.c",
        "pngstruct.h",
        "pngtrans.c",
        "pngwio.c",
        "pngwrite.c",
        "pngwtran.c",
        "pngwutil.c",
    ] + select({
        "@platforms//cpu:armv7": [
            "arm/arm_init.c",
            "arm/filter_neon.S",
            "arm/filter_neon_intrinsics.c",
            "arm/palette_neon_intrinsics.c",
        ],
        "@platforms//cpu:arm64": [
            "arm/arm_init.c",
            "arm/filter_neon.S",
            "arm/filter_neon_intrinsics.c",
            "arm/palette_neon_intrinsics.c",
        ],
        "@platforms//cpu:x86_32": [
            "intel/filter_sse2_intrinsics.c",
            "intel/intel_init.c",
        ],
        "@platforms//cpu:x86_64": [
            "intel/filter_sse2_intrinsics.c",
            "intel/intel_init.c",
        ],
        "//conditions:default": [],
    }),
    hdrs = [
        "png.h",
        "pngconf.h",
    ],
    includes = ["."],
    linkopts = [
        "-lm",
        "-lz",  # not sure this is needed
    ] + select({
        "@platforms//os:android": [],
        "//conditions:default": [],
    }),
    visibility = ["//visibility:public"],
    # deps = ["@zlib//:zlib"],
)
