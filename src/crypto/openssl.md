# openssl

## 1. 生成私钥
```
openssl genrsa -out private.pem 2048
```

## 2. 基于私钥生成公钥
```
openssl rsa -in private.pem -pubout -out public.pem
```

## 3. 查看 ASN.1 格式的私钥
```
openssl asn1parse -i -in private.pem
```

## 4. 查看 ASN.1 格式的公钥
```
openssl asn1parse -i -in public.pem
openssl asn1parse -i -in public.pem -strparse 16
```

## 5. 对文件 hello.txt 加密
```
openssl rsautl -encrypt -in hello.txt -inkey public.pem -pubin -out hello.en
```

## 6. 对文件 hello.en 解密
```
openssl rsautl -decrypt -in hello.en -inkey private.pem -out hello.de
```