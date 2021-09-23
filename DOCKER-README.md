# A RMTP streaming ready image with demo content with ffmpeg

This docker image is targeted to provide ready streaming content along with ffmpeg.

Based on the
[opencoconut/ffmpeg](https://hub.docker.com/r/opencoconut/ffmpeg) image developed by **Bruno Celeste** (@brunoceleste)

Available at GitHub: [neymoura/streaming-machine](https://github.com/neymoura/streaming-machine)

# Available content

- Big Buck Bunny:
    - File on image: `/streaming/videos/bbb.flv`
    - Available at: https://peach.blender.org
    - Blender Foundation | www.blender.org

- Sintel:
    - File on image: `/streaming/videos/sintel.flv`
    - Available at: https://durian.blender.org
    - © copyright Blender Foundation | durian.blender.org

# Usage

General usage:
```shell
$ docker run neymoura/streaming-machine ffmpeg -re -i ${STREAM_FILE} -c copy -f flv ${STREAM_RMTP}
```

Big Buck Bunny:
```shell
$ docker run neymoura/streaming-machine ffmpeg -re -i /streaming/videos/bbb.flv -c copy -f flv ${STREAM_RMTP}
```

Sintel:
```shell
$ docker run neymoura/streaming-machine ffmpeg -re -i /streaming/videos/sintel.flv -c copy -f flv ${STREAM_RMTP}
```

# Using docker compose

Running one stream:
```yaml
services:
  streaming-machine:
    image: neymoura/streaming-machine:1.0.0
    env_file: .env
    entrypoint: ffmpeg -re -i /streaming/videos/sintel.flv -c copy -f flv ${STREAM_RMTP}
```

Running two streams:
```yaml
services:
  stream-one:
    image: neymoura/streaming-machine:1.0.0
    env_file: .env
    entrypoint: ffmpeg -re -i /streaming/videos/sintel.flv -c copy -f flv ${STREAM_ONE_RMTP}
  stream-two:
    image: neymoura/streaming-machine:1.0.0
    env_file: .env
    entrypoint: ffmpeg -re -i /streaming/videos/bbb.flv -c copy -f flv ${STREAM_TWO_RMTP}
```

# Author

Ney Moura

https://github.com/neymoura