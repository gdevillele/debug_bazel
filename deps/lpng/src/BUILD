load("@rules_cc//cc:defs.bzl", "cc_library", "cc_binary")
load("@emsdk//emscripten_toolchain:wasm_rules.bzl", "wasm_cc_binary")

cc_library(
    name = "headers",
    hdrs = [
        "png.h",
        "pngconf.h",
    ],
    visibility = ["//visibility:public"],
    deps = ["@zlib//:zlib"],
)

cc_binary(
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
    ],
    includes = ["."],
    linkopts = [
        "-s",
        "FILESYSTEM=0",
        "-s",
        "ENVIRONMENT=web",
        "-s",
        "MINIMAL_RUNTIME=1",
        # "-s",
        # "LINKABLE=1",
        "-s",
        "EXPORTED_FUNCTIONS=[" +
            "\"_png_create_png_struct\"" +
        "]",
        # "EXPORTED_FUNCTIONS=[\"_png_create_png_struct\"]",
    ],
    visibility = ["//visibility:public"],
    deps = [
        ":headers",
        "@zlib//:zlib"
    ],
)

wasm_cc_binary(
    name = "wasm",
    cc_target = ":png",
    visibility = ["//visibility:public"],
)
