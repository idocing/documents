# test

## show output
```shell
cargo test -- --show-output
```

## assert
```rust
#[test]
fn test_xxx() {
    assert!(true)
    assert_eq!(0, 1)
    assert_ne!(0, 1)
}
```

## should panic
```rust
#[test]
#[should_panic]
fn test_xxx() {
    assert!(true)
}
```
