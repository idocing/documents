# rustup

## install rustup online
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

## install rustup offline
- visit rustup.rs
- download rustup-init


## rustup install
```
Update Rust toolchains

Usage: rustup install [OPTIONS] <toolchain>...

Arguments:
  <toolchain>...  Toolchain name, such as 'stable', 'nightly', or '1.0.0'. For more information see `rustup help toolchain`

Options:
      --profile <profile>  [possible values: minimal, default, complete]
      --no-self-update     Don't perform self-update when running the `rustup install` command
      --force              Force an update, even if some components are missing
      --force-non-host     Install toolchains that require an emulator. See https://github.com/rust-lang/rustup/wiki/Non-host-toolchains
  -h, --help               Print help

Discussion:
    Installs a specific rust toolchain.

    The 'install' command is an alias for 'rustup update <toolchain>'.
```
