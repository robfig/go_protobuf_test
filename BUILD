package(default_visibility = ["//visibility:public"])

load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_test")

load("@org_pubref_rules_protobuf//go:rules.bzl", "go_proto_library")

#
# Demonstration of importing the protobuf well-known types.
#

go_proto_library(
    name = "protolib",
    protos = ["wkt.proto"],
    importpath = "github.com/pubref/rules_protobuf/examples/wkt/go/protolib",
    imports = [
        'external/com_github_protocolbuffers_protobuf/src',
    ],
    importmap = {
        'google/protobuf/descriptor.proto': 'github.com/golang/protobuf/protoc-gen-go/descriptor',
        'google/protobuf/compiler/plugin.proto': 'github.com/golang/protobuf/protoc-gen-go/plugin',
    },
    inputs = [ "@com_github_protocolbuffers_protobuf//:well_known_protos" ],
    deps = [
        "@com_github_golang_protobuf//ptypes/any:go_default_library",
        "@com_github_golang_protobuf//ptypes/duration:go_default_library",
        "@com_github_golang_protobuf//ptypes/timestamp:go_default_library",
        "@com_github_golang_protobuf//ptypes/empty:go_default_library",
        "@com_github_golang_protobuf//ptypes/struct:go_default_library",
        "@com_github_golang_protobuf//ptypes/wrappers:go_default_library",
        "@com_github_golang_protobuf//protoc-gen-go/descriptor:go_default_library",
        "@com_github_golang_protobuf//protoc-gen-go/plugin:go_default_library",
    ],
)

go_test(
    name = "wkt_test",
    size = "small",
    srcs = ["wkt_test.go"],
    deps = [
        "protolib",
        "@com_github_golang_protobuf//protoc-gen-go/descriptor:go_default_library",
    ],
)
