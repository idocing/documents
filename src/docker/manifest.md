# manifest

## pull images and tag
```
docker pull alpine:latest@sha256:e7d88de73db3d3fd9b2d63aa7f447a10fd0220b7cbf39803c803f2af9ba256b3
docker tag xxx irepoing/alpine:3-amd
docker push irepoing/alpine:3-amd

docker pull alpine:latest@sha256:c74f1b1166784193ea6c8f9440263b9be6cae07dfe35e32a5df7a31358ac2060
docker tag yyy irepoing/alpine:3-arm
docker push irepoing/alpine:3-arm
```

## create manifest
```
docker manifest create irepoing/alpine:3 irepoing/alpine:3-amd irepoing/alpine:3-arm
```

## annotate manifest
```
docker manifest annotate irepoing/alpine:3 irepoing/alpine:3-amd --os linux --arch amd64
docker manifest annotate irepoing/alpine:3 irepoing/alpine:3-arm --os linux --arch arm64
```

## push manifest
```
docker manifest push irepoing/alpine:3
```