workspace(name = "angular_bazel_architect")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "dd7ea7efda7655c218ca707f55c3e1b9c68055a70c31a98f264b3445bc8f4cb1",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/3.2.3/rules_nodejs-3.2.3.tar.gz"],
)

load("@build_bazel_rules_nodejs//:index.bzl", "yarn_install")

yarn_install(
    name = "npm",
    data = ["//:patches/@angular-devkit+architect-cli+0.1102.6.patch"],
    package_json = "//:package.json",
    # Turn off symlink_node_modules here as it causes extreme flakiness on buildkite
    # macos CI with missing files in node_modules.
    # TODO: track down the root cause of the flakiness; it may be something to
    # do with how the Bazel team has setup their macos virtualization.
    symlink_node_modules = False,
    yarn_lock = "//:yarn.lock",
)
