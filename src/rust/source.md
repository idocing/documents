# source

## default
```toml
[source.crates-io]
registry = "https://github.com/rust-lang/crates.io-index"
```

## other
```toml
[source.crates-io]
replace-with = "vendor"

[source.vendor]
directory = "/path/vendor"

[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"

[source.localreg]
local-registry = "/path/localreg"

[source.remote]
git = "https://github.com/remote"
branch = "dev"
tag = "v1.0.0"
rev = "abc001"
```
