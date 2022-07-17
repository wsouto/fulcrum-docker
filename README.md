# fulcrum-docker

Build a Docker image for Fulcrum from source and run it using a docker-compose.yml file.

* Fulcrum repo: https://github.com/cculianu/Fulcrum
* Docker images: https://hub.docker.com/r/waltersouto/fulcrum

## How to use:

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
- Apply the patch to make only the linux image:
```
git apply ../docker.patch
```
- Build the image (it may take a while):
```
contrib/docker/build.sh fulcrum:v1.7.0
```
- Edit the `docker-compose.yml` to use your image.
- Do the step **1** from here.
