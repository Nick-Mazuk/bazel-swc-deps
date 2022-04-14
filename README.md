# bazel-swc-es6

In this repo:

- `package-a` depends on `package-b`
- `package-b` depends on `package-c`
- `package-c` has no dependencies

So when you build `package-a`, you'd expect both `package-b` and `package-c` to be built. However, that's not the case when using `swc_transpiler`.

Run:

```bash
bazel clean # in case there are any existing build artifacts
bazel build //package-a
```

Then look at `./bazel-bin`, and notice how `package-c` was not built.
