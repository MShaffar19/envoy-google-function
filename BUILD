package(default_visibility = ["//visibility:public"])

load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_binary",
    "envoy_cc_library",
    "envoy_cc_test",
)

envoy_cc_binary(
    name = "envoy",
    repository = "@envoy",
    deps = [
        ":gfunction_filter_config",
        "@envoy//source/exe:envoy_main_entry_lib",
    ],
)


envoy_cc_library(
    name = "google_authenticator_lib",
    srcs = ["google_authenticator.cc"],
    hdrs = ["google_authenticator.h"],
    repository = "@envoy",
    deps = [
        "@envoy//source/exe:envoy_common_lib",
    ],
)

envoy_cc_library(
    name = "gfunction_filter_lib",
    srcs = ["gfunction_filter.cc"],
    hdrs = ["gfunction_filter.h"],
    repository = "@envoy",
    deps = [
        ":google_authenticator_lib",        
        "@envoy//source/exe:envoy_common_lib",
    ],
)

envoy_cc_library(
    name = "gfunction_filter_config",
    srcs = ["gfunction_filter_config.cc"],
    repository = "@envoy",
    deps = [
        ":gfunction_filter_lib",
        "@envoy//source/exe:envoy_common_lib",
    ],
)

envoy_cc_test(
    name = "gfunction_filter_integration_test",
    srcs = ["gfunction_filter_integration_test.cc"],
    data = [":envoy-test.conf"],
    repository = "@envoy",
    deps = [
        ":gfunction_filter_config",
        "@envoy//test/integration:integration_lib",
        "@envoy//test/integration:http_integration_lib"
    ],
)