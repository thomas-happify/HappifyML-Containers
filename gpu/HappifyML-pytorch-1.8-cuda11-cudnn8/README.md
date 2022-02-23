

1. Build
```bash
docker build --tag thomasyue/happifyml:HappifyML-pytorch-1.8-cuda11-cudnn8 -f Dockerfile.azure .
```

2. Push to docker hub
```
docker push thomasyue/happifyml:HappifyML-pytorch-1.8-cuda11-cudnn8
```