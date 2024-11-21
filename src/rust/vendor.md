# vendor

## generate vendor
```
cargo vendor
```

## use vendor
```
[source.crates-io]
registry = "https://github.com/rust-lang/crates.io-index"
replace-with = "rsproxy"

[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"
replace-with = "local"

[source.local]
directory = "vendor"
```
