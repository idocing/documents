# registry

## index
```
https://index.crates.io
```

## default registries
```toml
[registries.crates-io]
index = "https://github.com/rust-lang/crates.io-index"
protocol = "sparse"
token = "xxx"

[registry]
default = "crates-io"
```

## other registries
```toml
[registries.rsproxy]
index = "https://rsproxy.cn/crates.io-index"
token = "xxx"

[registry]
default = "rsproxy"
```
