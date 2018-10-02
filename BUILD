package(default_visibility = ["//visibility:public"])

load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_test")
load("@org_pubref_rules_protobuf//gogo:rules.bzl", "gogo_proto_library")

#
# Demonstration of importing the protobuf well-known types.
#

gogo_proto_library(
    name = "protolib",
    importmap = {
        "google/protobuf/any.proto": "github.com/gogo/protobuf/ptypes/any",
        "google/protobuf/descriptor.proto": "github.com/gogo/protobuf/protoc-gen-go/descriptor",
        "google/protobuf/duration.proto": "github.com/gogo/protobuf/ptypes/duration",
        "google/protobuf/empty.proto": "github.com/gogo/protobuf/ptypes/empty",
        "google/protobuf/struct.proto": "github.com/gogo/protobuf/ptypes/struct",
        "google/protobuf/timestamp.proto": "github.com/gogo/protobuf/ptypes/timestamp",
        "google/protobuf/wrappers.proto": "github.com/gogo/protobuf/ptypes/wrappers",
    },
    importpath = "github.com/pubref/rules_protobuf/examples/wkt/go/protolib",
    imports = [
        "external/com_github_gogo_protobuf/protobuf",
    ],
    inputs = [
        "@com_github_gogo_protobuf//protobuf/google/protobuf:go_default_library_protos",
        "@com_github_gogo_protobuf//protobuf/google/protobuf/compiler:go_default_library_protos",
    ],
    protos = ["wkt.proto"],
    deps = [
        "@com_github_gogo_protobuf//proto:go_default_library",
        "@com_github_gogo_protobuf//proto/proto3_proto:go_default_library",
        "@com_github_gogo_protobuf//types:go_default_library",
    ],
)

go_test(
    name = "wkt_test",
    size = "small",
    srcs = ["wkt_test.go"],
    deps = [
        "protolib",
        "@com_github_gogo_protobuf//protoc-gen-gogo/descriptor:go_default_library",
    ],
)
