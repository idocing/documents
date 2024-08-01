# export

## export class
```
class __declspec(dllexport) XXX {
    public:
        XXX();
        
        ~XXX();

        void xxx();
};
```

## export function
```
extern "C" __declspec(dllexport) void xxx();
```