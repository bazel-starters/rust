"""
Build supporting tools.

The tools subpackage is used to define build rules and configurations for tools
used throughout the repository. Firstparty tools not required for build support
should live elsewhere.

Of special note is that we're using the `bazel_env.bzl` tool to re-export tools
used under Bazel as a `bin/` tree which can be added to the `$PATH`. The
included `.envrc` automates this for you.

"""

load("@bazel_env.bzl", "bazel_env")
load("@bazelrc-preset.bzl", "bazelrc_preset")
load("@multitool//:tools.bzl", MULTITOOL_TOOLS = "TOOLS")

package(default_visibility = ["//visibility:public"])

bazelrc_preset(name = "preset")

bazel_env(
    name = "bazel_env",
    toolchains = {
        "rust": "@rules_rust//rust/toolchain:current_rust_toolchain",
    },
    tools = {
        # Mapping from tool binary name ($PATH entry) to Bazel label
        "buildifier": "@buildifier_prebuilt//:buildifier",
        "cargo": "$(CARGO)",
    } | MULTITOOL_TOOLS,
)
