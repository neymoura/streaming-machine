# Streaming Machine

The streaming machine is a set of a docker image and a docker compose to achieve the simpliest way to stream demo content into a RMTP url.

Available at Docker Hub:
[neymoura/streaming-machine](https://hub.docker.com/r/neymoura/streaming-machine)

# Quick start

Using the docker image: `neymoura/streaming-machine`

Create your `.env` file as:
```env
STREAM_ONE_FILE="/streaming/videos/bbb.flv"
STREAM_ONE_RMTP="rtmp://url-one"
STREAM_TWO_FILE="/streaming/videos/sintel.flv"
STREAM_TWO_RMTP="rtmp://url-two"
```

Then run:
```shell
docker compose up
```

The image will start streaming both contents on both RMTP Urls.

# Custom usage

## Enviroment setup

Create the `.env` file with the contents of `.env.example` to setup the environment like:
```shell
STREAM_ONE_FILE="/streaming/videos/video1.flv"
STREAM_ONE_RMTP="rtmp://rtmp.sample.1"
STREAM_TWO_FILE="/streaming/videos/video2.flv"
STREAM_TWO_RMTP="rtmp://rtmp.sample.2"
```

The `STREAM_x_FILE` is the file wich will be streamed to the `STREAM_x_RMTP` url.

> :warning: By default, the docker compose file will read and stream those two streams. Feel free to change this as needed.

## Change `docker-compose.yml`

Currently the docker-compose is using the public image, so you must replace the `image: neymoura/streaming-machine:1.0.0` to `build: .` to build the image locally.

The `docker-compose.yml` should look like this:

```yml
services:
  stream-one:
    build: .
    env_file: .env
    entrypoint: ffmpeg -re -i ${STREAM_ONE_FILE} -c copy -f flv ${STREAM_ONE_RMTP}
  stream-two:
    build: .
    env_file: .env
    entrypoint: ffmpeg -re -i ${STREAM_TWO_FILE} -c copy -f flv ${STREAM_TWO_RMTP}
```

## Video

Please add your video files in the `/videos` directory and specify those files in the `.env` file.

When building the image docker will copy all the files inside `/videos` to the `/streaming/videos/` directory inside the image.

> :warning: .flv files are preferred for greater performance

## Running

```shell
docker compose up
```