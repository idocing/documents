# source

## default
```toml
[source.crates-io]
registry = "https://github.com/rust-lang/crates.io-index"
```

## other
```toml
[source.crates-io]
replace-with = "rsproxy"

[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"

[source.local]
directory = "vendor"

[source.remote]
git = "https://github.com/remote"
```
