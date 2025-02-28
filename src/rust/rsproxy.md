# rsproxy  

## step 1
```shell
export RUSTUP_UPDATE_ROOT=https://rsproxy.cn/rustup
export RUSTUP_DIST_SERVER=https://rsproxy.cn
```

```shell
export RUSTUP_UPDATE_ROOT=https://mirrors.aliyun.com/rustup/rustup
export RUSTUP_DIST_SERVER=https://mirrors.aliyun.com/rustup
```

## step 2
```shell
curl --proto '=https' --tlsv1.2 -sSf https://rsproxy.cn/rustup-init.sh | sh
```

```shell
curl --proto '=https' --tlsv1.2 -sSf https://mirrors.aliyun.com/repo/rust/rustup-init.sh | sh
```

## step 3
> vi ~/.cargo/config.toml
```toml
[net]
git-fetch-with-cli = true

[cargo-new]
vcs = "none"

[registries.crates-io]
index = "https://github.com/rust-lang/crates.io-index"

[registries.rsproxy]
index = "https://rsproxy.cn/crates.io-index"

[registry]
default = "rsproxy"

[source.crates-io]
replace-with = "rsproxy-sparse"

[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"

[source.rsproxy-sparse]
registry = "sparse+https://rsproxy.cn/index/"
```

```toml
[source.crates-io]
replace-with = 'aliyun'
[source.aliyun]
registry = "sparse+https://mirrors.aliyun.com/crates.io-index/"
```