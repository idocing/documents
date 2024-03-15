# vscode golang

## go extension
```
https://marketplace.visualstudio.com/items?itemName=golang.go
```

## settings.json
```
{
    "go.goroot": "/path/go",
    "go.gopath": "/home/c/go",
    "go.gotoSymbol.includeGoroot": true,
    "go.toolsManagement.autoUpdate": true,
}
```

## go plugin (go:install/update)
```
go install github.com/go-delve/delve/cmd/dlv@latest
go install golang.org/x/tools/gopls@latest
go install github.com/josharian/impl@latest
go install github.com/cweill/gotests/gotests@latest
go install github.com/haya14busa/goplay/cmd/goplay@latest
go install github.com/ramya-rao-a/go-outline@latest
go install github.com/fatih/gomodifytags@latest
go install honnef.co/go/tools/cmd/staticcheck@latest
```