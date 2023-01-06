# Example cargo workspace demonstrating wierd linking issue

## To reproduce error:

```
cargo build # in root folder of repo
```

Should give the following output:

```
error: Attempting to resolve a dependency with more than one crate with links=m.
This will not build as is. Consider rebuilding the .lock file.
```

## To build executable-a and executable-b:


```
mv Cargo.toml Carg.toml.bak
cd executable-a
cargo build
cd ../executable-b
cargo build
```

## Why is this wierd?

It is strange that it is possible to build `executable-a` and `executable-b` as stand alone crates,
but the minute they are in a workspace, they will not compile.
Even though the two executables have no shared code.
