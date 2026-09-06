# greet

The first ever Kex library package.

## Use it in your own package

From inside your package, add it as a Git dependency:

```sh
tey add greet --git https://github.com/kexhq/greet --tag "~> 0.1"
```

That appends the dependency to `package.kex` and resolves `tey.lock` in one
step:

```kex
bundle "yours" do
  ...
  tey("greet", git: "https://github.com/kexhq/greet", tag: "~> 0.1")
end
```

`~> 0.1` accepts any `0.1.x` release, so patch fixes arrive without a manifest
edit while `0.2.0` does not. Use `--branch` or `--ref` instead of `--tag` to
track a branch or pin one commit.

`tey.lock` records the exact commit and a `sha256` of the resolved source, and
is verified on every install — commit it. Then fetch and use it:

```sh
tey install
```

```kex
using Greet

main do
  Greet.hello               # prints: Hello, World!
  Greet.greet("Ákos")       # prints: Hello, Ákos!
  IO.printLine(Greet.greeting("Kex"))
end
```

`greeting/1` returns the string; `greet/1` and `hello` print it.

## Develop

```sh
tey install   # fetch dependencies
tey build     # compile into ebin/
tey test      # run spec/*.spec.kex
```

## Run it

```sh
tey install
tey run
```
