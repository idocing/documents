# rsproxy  

## step 1
```
export RUSTUP_UPDATE_ROOT=https://rsproxy.cn/rustup
export RUSTUP_DIST_SERVER=https://rsproxy.cn
```

## step 2
```
curl --proto '=https' --tlsv1.2 -sSf https://rsproxy.cn/rustup-init.sh | sh
```

## step 3
    > vi ~/.cargo/config.toml
```
[net]
git-fetch-with-cli = true

[cargo-new]
vcs = "none"

[registries.zero]
index = "https://github.com/rust-lang/crates.io-index"

[registries.rsproxy]
index = "https://rsproxy.cn/crates.io-index"

[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"

[source.rsproxy-sparse]
registry = "sparse+https://rsproxy.cn/index/"

[source.crates-io]
replace-with = "rsproxy-sparse"
```
