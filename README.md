# StaticJinjaPlus Docker Images

This repository provides Docker images for [StaticJinjaPlus](https://github.com/MrDave/StaticJinjaPlus), 
a powerful static site generator. The images are available with various tags and optimized for different purposes: 
based on Python 3.11 builds, based on Ubuntu 22.04, and development images.

All images are available on [DockerHub](https://hub.docker.com/repository/docker/sigvard/static-jinja-plus/general).

---

## Available Versions

### Tags
- **`latest`**: The latest stable release of StaticJinjaPlus, based on Ubuntu 22.04.
- **`slim`**: The latest stable release, based on Python 3.11.
- **`develop`**: A development image with the latest features from the main branch, based on Ubuntu 22.04.
- **`develop-slim`**: A development image with the latest features from the main branch, based on Python 3.11.
- **`0.1.1`**: Release version 0.1.1, based on Ubuntu 22.04.
- **`0.1.1-slim`**: Release version 0.1.1, based on Python 3.11.
- **`0.1.0`**: Release version 0.1.0, based on Ubuntu 22.04.
- **`0.1.0-slim`**: Release version 0.1.0, based on Python 3.11.

---

## Pulling the Images

You can pull any image using the following commands:

```bash
# Pull the latest stable image (Ubuntu 22.04)
docker pull sigvard/static-jinja-plus:latest

# Pull the latest stable image (Python 3.11)
docker pull sigvard/static-jinja-plus:slim

# Pull the development image (Ubuntu 22.04)
docker pull sigvard/static-jinja-plus:develop

# Pull the development image (Python 3.11)
docker pull sigvard/static-jinja-plus:develop-slim

# Pull a specific version (e.g., 0.1.1, Ubuntu 22.04)
docker pull sigvard/static-jinja-plus:0.1.1

# Pull a lightweight version (e.g., 0.1.1-slim, Python 3.11)
docker pull sigvard/static-jinja-plus:0.1.1-slim
```

---

## Usage

### Basic Usage

To run the container and generate templates, use the following command:
```bash
docker run -v /path/to/templates:/app/templates -v /path/to/build:/app/build sigvard/static-jinja-plus:latest
```

Replace /path/to/templates with the path to your templates directory and 
/path/to/build with the path to your build directory.

### Advanced Usage

For development, you can use the develop tag to test the latest features:

```bash
docker run -v /path/to/templates:/app/templates -v /path/to/build:/app/build sigvard/static-jinja-plus:develop
```

For a version with faster startup time, use a slim tag:
```bash
docker run -v /path/to/templates:/app/templates -v /path/to/build:/app/build sigvard/static-jinja-plus:slim
```


## Building the Images

If you want to build the Docker images yourself, follow these steps:

Clone the repository:

```bash
git clone https://github.com/MrDave/StaticJinjaPlus.git
cd StaticJinjaPlus
```

Build the image:

```bash
docker build -t ${DOCKER_USERNAME}/${IMAGE_NAME}:${TAG} -f ${PART_TO_DOCKERFILE} . --build-arg SJP_TAG=${SJP_TAG} --build-arg SJP_HASH=${SJP_HASH}
```

- ${SJP_TAG} - tag from the [StaticJinjaPlus](https://github.com/MrDave/StaticJinjaPlus) repository (0.1.1 default)
- ${SJP_HASH} - hash sum of file 
```bash 
curl -sL https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/${SJP_TAG}.tar.gz | sha256sum
```
