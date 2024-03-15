# algorithm

## flat_to_nest

```
const test_data = [
    { pid: 0, id: 1, name: "aaa" },
    { pid: 0, id: 2, name: "bbb" },
    { pid: 1, id: 3, name: "ccc" },
    { pid: 2, id: 4, name: "ddd" },
    { pid: 3, id: 5, name: "eee" },
]
export const flat_to_nest = function (data) {
    if (!data) {
        data = test_data
    }
    let res = []
    data.forEach(c => {
        c.children = []
        if (c.pid == 0) {
            res.push(a)
        } else {
            data.find(it => {
                return it.id === c.pid
            }).children.push(c)
        }
    })
    return res
}
```