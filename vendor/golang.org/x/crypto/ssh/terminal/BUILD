load("@io_bazel_rules_go//go:def.bzl", "go_library")

go_library(
    name = "go_default_library",
    srcs = [
        "terminal.go",
    ] + select({
        "@io_bazel_rules_go//go/platform:darwin_amd64": [
            "util.go",
            "util_bsd.go",
        ],
        "@io_bazel_rules_go//go/platform:linux_amd64": [
            "util.go",
            "util_linux.go",
        ],
        "@io_bazel_rules_go//go/platform:windows_amd64": [
            "util_windows.go",
        ],
        "//conditions:default": [],
    }),
    importpath = "golang.org/x/crypto/ssh/terminal",
    visibility = ["//visibility:public"],
    deps = select({
        "@io_bazel_rules_go//go/platform:darwin_amd64": [
            "//vendor/golang.org/x/sys/unix:go_default_library",
        ],
        "@io_bazel_rules_go//go/platform:linux_amd64": [
            "//vendor/golang.org/x/sys/unix:go_default_library",
        ],
        "@io_bazel_rules_go//go/platform:windows_amd64": [
            "//vendor/golang.org/x/sys/windows:go_default_library",
        ],
        "//conditions:default": [],
    }),
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [":package-srcs"],
    tags = ["automanaged"],
    visibility = ["//visibility:public"],
)
