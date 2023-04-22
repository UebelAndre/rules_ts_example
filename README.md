# rules_ts_example

This repo is an example of code that passes `tsc` when run with `pnpm` but fails when run with Bazel using [rules_ts](https://github.com/aspect-build/rules_ts).

## PNPM

```
~/Code/rules_ts_example/foo (main ✗) pnpm run build

> @rules_ts_example/foo@1.0.0 build /Users/user/Code/rules_ts_example/foo
> tsc

```

## BAZEL

```
~/Code/rules_ts_example (main ✗) bazel build //...
INFO: Analyzed 3 targets (1 packages loaded, 50 targets configured).
INFO: Found 3 targets...
ERROR: /Users/user/Code/rules_ts_example/foo/BUILD.bazel:11:11: Compiling TypeScript project @//foo:foo_ts [tsc -p foo/tsconfig.json] failed: (Exit 1): tsc.sh failed: error executing command (from target //foo:foo_ts)
  (cd /private/var/tmp/_bazel_user/729471d7b159995c3ffbf36ad2691a5e/sandbox/darwin-sandbox/300/execroot/rules_ts_example && \
  exec env - \
    BAZEL_BINDIR=bazel-out/darwin_arm64-fastbuild/bin \
  bazel-out/darwin_arm64-opt-exec-2B5CBBC6/bin/external/npm_typescript/tsc.sh --project foo/tsconfig.json --outDir foo --rootDir foo --declarationDir foo --tsBuildInfoFile foo/foo_ts.tsbuildinfo)
# Configuration: 0ba77a61754b8ccac68b4c11211b3ebeca24c2f07acb9bc57df3ce73dcecadb5
# Execution platform: @local_config_platform//:host

Use --sandbox_debug to see verbose messages from the sandbox and retain the sandbox build root for debugging
foo/src/index.tsx(40,10): error TS2786: 'Head' cannot be used as a JSX component.
  Its instance type 'Head' is not a valid JSX element.
    Type 'Head' is missing the following properties from type 'ElementClass': setState, forceUpdate, props, state, refs
foo/src/index.tsx(50,18): error TS2339: Property 'props' does not exist on type 'MyDocument'.
foo/src/index.tsx(55,12): error TS2786: 'NextScript' cannot be used as a JSX component.
  Its instance type 'NextScript' is not a valid JSX element.
    Type 'NextScript' is missing the following properties from type 'ElementClass': setState, forceUpdate, props, state, refs
INFO: Elapsed time: 3.645s, Critical Path: 3.19s
INFO: 2 processes: 2 internal.
FAILED: Build did NOT complete successfully
```
