# rust build

## link library

### gnu

> build.rs
```
println!("cargo:rustc-link-search=native=./lib");
println!("cargo:rustc-link-lib=dylib=xxx");
```

> .cargo/config.toml
```
[build]
rustflags = ["-L./lib", "-lxxx"]
```

### msvc

> the import library name should be "xxx.lib"  
> the dynamic library name should be "xxx.dll"