licenses(["notice"])  # Apache 2

load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_binary",
    "envoy_cc_fuzz_test",
    "envoy_cc_test",
    "envoy_cc_test_library",
    "envoy_package",
    "envoy_proto_library",
)

envoy_package()

envoy_proto_library(
    name = "access_log_formatter_fuzz_proto",
    srcs = ["access_log_formatter_fuzz.proto"],
    deps = ["//test/fuzz:common_proto"],
)

envoy_cc_fuzz_test(
    name = "access_log_formatter_fuzz_test",
    srcs = ["access_log_formatter_fuzz_test.cc"],
    corpus = "access_log_formatter_corpus",
    deps = [
        ":access_log_formatter_fuzz_proto_cc_proto",
        "//source/common/access_log:access_log_formatter_lib",
        "//test/fuzz:utility_lib",
    ],
)

envoy_cc_test(
    name = "access_log_formatter_test",
    srcs = ["access_log_formatter_test.cc"],
    deps = [
        "//source/common/access_log:access_log_formatter_lib",
        "//source/common/common:utility_lib",
        "//source/common/http:header_map_lib",
        "//source/common/router:string_accessor_lib",
        "//test/mocks/http:http_mocks",
        "//test/mocks/ssl:ssl_mocks",
        "//test/mocks/stream_info:stream_info_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "access_log_impl_test",
    srcs = ["access_log_impl_test.cc"],
    deps = [
        "//source/common/access_log:access_log_lib",
        "//source/extensions/access_loggers/file:config",
        "//test/common/stream_info:test_util",
        "//test/common/upstream:utility_lib",
        "//test/mocks/access_log:access_log_mocks",
        "//test/mocks/event:event_mocks",
        "//test/mocks/filesystem:filesystem_mocks",
        "//test/mocks/runtime:runtime_mocks",
        "//test/mocks/server:server_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "access_log_manager_impl_test",
    srcs = ["access_log_manager_impl_test.cc"],
    deps = [
        "//source/common/access_log:access_log_manager_lib",
        "//source/common/stats:isolated_store_lib",
        "//source/common/stats:stats_lib",
        "//test/mocks/access_log:access_log_mocks",
        "//test/mocks/api:api_mocks",
        "//test/mocks/event:event_mocks",
        "//test/mocks/filesystem:filesystem_mocks",
    ],
)

envoy_cc_binary(
    name = "access_log_formatter_speed_test",
    testonly = 1,
    srcs = ["access_log_formatter_speed_test.cc"],
    external_deps = [
        "benchmark",
    ],
    deps = [
        "//source/common/access_log:access_log_formatter_lib",
        "//source/common/http:header_map_lib",
        "//source/common/network:address_lib",
        "//test/common/stream_info:test_util",
        "//test/mocks/http:http_mocks",
        "//test/mocks/stream_info:stream_info_mocks",
        "//test/test_common:printers_lib",
    ],
)
