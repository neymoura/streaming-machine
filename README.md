# Streaming Machine

The streaming machine is a set of a docker image and a docker compose to achieve the simpliest way to stream demo content into a RMTP url.

# Usage

## Enviroment setup

Create the `.env` file with the contents of `.env.example` to setup the environment like:
```shell
STREAM_ONE_FILE="/streaming/videos/video1.flv"
STREAM_ONE_RMTP="rtmp://rtmp.sample.1"
STREAM_TWO_FILE="/streaming/videos/video2.flv"
STREAM_TWO_RMTP="rtmp://rtmp.sample.2"
```

The `STREAM_x_FILE` is the file wich will be streamed to the `STREAM_x_RMTP` url.

> :info: By default, the docker compose file will read and stream those two streams. Feel free to change this as needed.

## Run compose

Just run:
```shell
docker compose up
```