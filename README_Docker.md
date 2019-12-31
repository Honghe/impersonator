# Nvidia Docker Build and Run
## Steps
1. Build the base docker image.
```
cd dockerbase
docker build -t impersonator/base_dev:1.0 .
```
2. Build the docker image with thirdparty.
```
cd thirdparty/neural_renderer
docker build -t impersonator/thirdparty:1.0
```
3. Run demo
```
docker run --shm-size 8G --rm -it -v /impersonator/:/impersonator/ impersonator/thirdparty:1.0 \
/bin/sh -c "cd impersonator && python demo_imitator.py"
```

## Notes
- Use `nvidia/cuda:10.0-cudnn7-devel-ubuntu16.04` as base docker image, cause the `thirdparty/neural_renderer` need Nvidia `nvcc`, and the `devel` images contains it.
- Use `ubuntu16.04` and `python3.6` to fit the environment of the author.
- Theses Docker images are for develop, not for production, so the Dockerfiles are not written for slim size.