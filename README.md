# fulcrum-docker

Build a Docker image for Fulcrum from source and run it using a docker-compose.yml file.

* Fulcrum repo: https://github.com/cculianu/Fulcrum
* Docker images: https://hub.docker.com/r/waltersouto/fulcrum

## How to use:

_**Note**: the Dockerfile used here is the one that comes with the source code and it builds two images being one for AMD64 and other for ARM64 architectures. The process used to build this two images pushes the images to the Docker Hub, it not supports load them in the local env. For more info search for ´Buildkit and buildx on the Docker documentation._

Clone the repo or dowload only the files you need.

To use the `docker-compose.yml` from this repo you are going to need the `.env` file for the steps bellow. **Check this file first** and edit according to your local environment, then:

**1. If you just want to run Fulcrum:**

- Copy `fulcrum.conf` (you can config everything in it) and `banner.txt` to the `HOST_DATA_DIR`.
- Edit these files as you need. Have fun on your banner!
- Run `docker compose up` .

**2. If you want to build your own image:**

- Clone this repo first and go to the directory.
- Clone the Fulcrum repo like this:
```
git clone https://github.com/cculianu/Fulcrum.git --single-branch source
```
- Go to the source directory: `cd source`.
- Opcionally check out this commit (look at the Fulcrum repo for more info):
```
git checkout 549cd23cd3a4346455f5113ef7e1d3e86599c51e
```
- Apply the patch to add support for read Fulcrum config file:
```
git apply ../docker.patch
```
- Build the images (read the note above if did not!). It may take a while:
```
contrib/docker/build.sh <your-docker-hub-repo>/fulcrum:v1.7.0
```
- Edit the `docker-compose.yml` to use your image from the Docker Hub.
- Do the step **1** from here.
