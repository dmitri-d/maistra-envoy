licenses(["notice"])  # Apache 2

# Access log implementation that calls into a WASM VM.

load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
    "envoy_package",
)

envoy_package()

envoy_cc_library(
    name = "wasm_access_log_lib",
    hdrs = ["wasm_access_log_impl.h"],
    deps = [
        "//include/envoy/access_log:access_log_interface",
        "//source/common/http:header_map_lib",
    ],
)

envoy_cc_library(
    name = "config",
    srcs = ["config.cc"],
    hdrs = ["config.h"],
    deps = [
        ":wasm_access_log_lib",
        "//include/envoy/registry",
        "//include/envoy/server:access_log_config_interface",
        "//source/common/access_log:access_log_formatter_lib",
        "//source/common/protobuf",
        "//source/extensions/access_loggers:well_known_names",
        "//source/extensions/common/wasm:wasm_lib",
        "@envoy_api//envoy/config/accesslog/v2:pkg_cc_proto",
    ],
)
