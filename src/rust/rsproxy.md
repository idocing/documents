# rsproxy  

## step 1
```
export RUSTUP_DIST_SERVER=https://rsproxy.cn
export RUSTUP_UPDATE_ROOT=https://rsproxy.cn/rustup
```

## step 2
```
curl --proto "=https" --tlsv1.2 -sSf https://rsproxy.cn/rustup-init.sh | sh
```

## step 3
    > vi ~/.cargo/config.toml
```
[net]
git-fetch-with-cli = true

[cargo-new]
vcs = "none"

[registries.rsproxy]
index = "https://rsproxy.cn/crates.io-index"

[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"

[source.rsproxy-sparse]
registry = "sparse+https://rsproxy.cn/index/"

[source.crates-io]
replace-with = "rsproxy-sparse"
```