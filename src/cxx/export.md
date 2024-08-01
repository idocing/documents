# export

## export function
```
extern "C" __declspec(dllexport) void xxx();
```

## export class
```
class __declspec(dllexport) XXX {
    public:
        XXX();
        
        ~XXX();

        void xxx();
};
```