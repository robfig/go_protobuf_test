package(default_visibility = ["//visibility:public"])

load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_test")

#
# Demonstration of importing the protobuf well-known types.
#

load("@com_github_pubref_rules_proto//github.com/gogo/protobuf:compile.bzl", "gogo_proto_compile")
load("@com_github_pubref_rules_proto//github.com/gogo/protobuf:library.bzl", "gogo_proto_library")

proto_library(
    name = "wkt_test_proto_library",
    srcs = ["wkt.proto"],
    deps = [
        "@com_github_protocolbuffers_protobuf//:any_proto",
        "@com_github_protocolbuffers_protobuf//:api_proto",
        "@com_github_protocolbuffers_protobuf//:compiler_plugin_proto",
        "@com_github_protocolbuffers_protobuf//:descriptor_proto",
        "@com_github_protocolbuffers_protobuf//:duration_proto",
        "@com_github_protocolbuffers_protobuf//:empty_proto",
        "@com_github_protocolbuffers_protobuf//:field_mask_proto",
        "@com_github_protocolbuffers_protobuf//:source_context_proto",
        "@com_github_protocolbuffers_protobuf//:struct_proto",
        "@com_github_protocolbuffers_protobuf//:timestamp_proto",
        "@com_github_protocolbuffers_protobuf//:type_proto",
        "@com_github_protocolbuffers_protobuf//:wrappers_proto",
    ],
)

gogo_proto_library(
    name = "protolib",
    srcs = [
        ":wkt_test_proto_library",
    ],
    importpath = "github.com/pubref/rules_protobuf/examples/wkt/go/protolib",
    deps = [
        "@com_github_golang_protobuf//protoc-gen-go/descriptor:go_default_library",
        "@com_github_golang_protobuf//protoc-gen-go/plugin:go_default_library",
        "@com_github_golang_protobuf//ptypes/any:go_default_library",
        "@com_github_golang_protobuf//ptypes/duration:go_default_library",
        "@com_github_golang_protobuf//ptypes/empty:go_default_library",
        "@com_github_golang_protobuf//ptypes/struct:go_default_library",
        "@com_github_golang_protobuf//ptypes/timestamp:go_default_library",
        "@com_github_golang_protobuf//ptypes/wrappers:go_default_library",
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
