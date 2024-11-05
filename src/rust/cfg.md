# cfg

## build.rs
```rust
println!("cargo:rustc-cfg=aaa");
println!("cargo:rustc-cfg=bbb=\"ccc\"");
```

## command line
```
cargo rustc -- --cfg aaa
cargo rustc -- --cfg bbb=\"ccc\"
```

## use cfg
```rust
fn task() {
    #[cfg(aaa)]
    {
        println!("aaa");
    }

    #[cfg(bbb="ccc")]
    {
        println!("bbb=ccc");
    }
}
```
