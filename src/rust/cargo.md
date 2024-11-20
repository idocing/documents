# cargo

## cargo install
```
cargo install --list
```

## cargo vendor

### make vendor
```
cargo vendor
```

### use vendor (.cargo/config.toml)
```
[source.local]
directory = "/path/vendor"

[source.crates-io]
replace-with = "local"
```
