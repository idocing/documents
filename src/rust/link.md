# link

## link c
> a. use attribute
```
#[link(name="tool", kind="dylib")]
extern "C" {
    #[link_name="kkk"]
    fn xxx();
}
```
- kind="dylib" #default
- kind="static"
- kind="framework"
- kind="raw-dylib"

> b. use link-arg (.cargo/config.toml)
```
[build]
rustflags = ["-L/path", "-ltool"] #linux
rustflags = ["-L/path", "-ltool.dll"] #windows
```

## build c
```
gcc -shared -o tool.so main.c
gcc -shared -Wl,--out-implib,tool.dll.lib -o tool.dll main.c
```

## build cxx
```
# export function
extern "C" __declspec(dllexport) void kkk();

g++ -shared -o tool.so main.c
g++ -shared -Wl,--out-implib,tool.dll.lib -o tool.dll main.cxx
```