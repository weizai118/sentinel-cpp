load("//bazel:copts.bzl", "DEFAULT_COPTS", "TEST_COPTS")

package(default_visibility = ["//visibility:public"])

cc_library(
  name = "record_log_interface",
  srcs = [
    "record_log.h",
  ],
  copts = DEFAULT_COPTS,
  deps = [
  ]
)

cc_library(
  name = "record_log_impl_lib",
  srcs = [
    "record_log.h",
    "record_log.cc",
  ],
  copts = DEFAULT_COPTS,
  deps = [
    "@com_github_gabime_spdlog//:spdlog"
  ]
)


cc_library(
  name = "log_base_interface",
  srcs = [
    "log_base.h",
  ],
  copts = DEFAULT_COPTS,
  deps = [
  ]
)

cc_library(
  name = "log_base_impl_lib",
  srcs = [
    "log_base.h",
    "log_base.cc",
  ],
  copts = DEFAULT_COPTS,
  deps = [
      "@com_google_absl//absl/strings",
      "//sentinel-core/utils:utils_lib",
      "//sentinel-core/utils:file_utils_lib",
      "//sentinel-core/init:init_target_registry_lib",
  ]
)

cc_library(
  name = "metric_lib",
  srcs = [
        "metric_writer.h",
        "metric_writer.cc",
        "metric_reader.h",
        "metric_reader.cc",
        "metric_searcher.h",
        "metric_searcher.cc",
  ],
  copts = DEFAULT_COPTS,
  deps = [
     "@com_google_absl//absl/strings",
     "//sentinel-core/utils:utils_lib",
     "//sentinel-core/utils:file_utils_lib",
     "//sentinel-core/statistic/base:metric_item_lib",
     "//sentinel-core/config:local_config_lib",
     ":record_log_impl_lib",
     ":log_base_impl_lib",
  ],
)


cc_test(
  name = "log_base_unittests",
  srcs = [
    "log_base_test.cc",
  ],
  copts = TEST_COPTS,
  deps = [
    ":log_base_impl_lib",
    "@com_google_googletest//:gtest_main",
  ]
)


cc_test(
  name = "metric_writer_unittests",
  srcs = [
    "metric_writer_test.cc",
  ],
  copts = TEST_COPTS,
  deps = [
    ":metric_lib",
    "@com_google_googletest//:gtest_main",
  ]
)

cc_test(
  name = "metric_reader_unittests",
  srcs = [
      "metric_test_utils.h",
    "metric_reader_test.cc",
  ],
  copts = TEST_COPTS,
  deps = [
    ":metric_lib",
    "@com_google_googletest//:gtest_main",
  ],
  linkstatic = 1,
)

cc_test(
  name = "metric_searcher_unittests",
  srcs = [
      "metric_test_utils.h",
    "metric_searcher_test.cc",
  ],
  copts = TEST_COPTS,
  deps = [
    ":metric_lib",
    "@com_google_googletest//:gtest_main",
  ],
  linkstatic = 1,
)