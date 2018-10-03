workspace(name = "go_protobuf_test")

http_archive(
    name = "io_bazel_rules_go",
    urls = ["https://github.com/bazelbuild/rules_go/releases/download/0.15.3/rules_go-0.15.3.tar.gz"],
    sha256 = "97cf62bdef33519412167fd1e4b0810a318a7c234f5f8dc4f53e2da86241c492",
)
load("@io_bazel_rules_go//go:def.bzl", "go_rules_dependencies", "go_register_toolchains")
go_rules_dependencies()
go_register_toolchains()

http_archive(
    name = "bazel_gazelle",
    urls = ["https://github.com/bazelbuild/bazel-gazelle/releases/download/0.14.0/bazel-gazelle-0.14.0.tar.gz"],
    sha256 = "c0a5739d12c6d05b6c1ad56f2200cb0b57c5a70e03ebd2f7b87ce88cabf09c7b",
)
load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies")
gazelle_dependencies()

git_repository(
  name = "com_github_pubref_rules_proto",
  remote = "https://github.com/robfig/rules_proto",
  commit = "6a85b0e4c3eeddf8863890ef48f2daab7a524ab7"
)

git_repository(
  name = "com_github_protocolbuffers_protobuf",
  remote = "https://github.com/protocolbuffers/protobuf",
  tag = "v3.6.1"
)
