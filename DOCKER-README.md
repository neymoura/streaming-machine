# A RMTP streaming ready image with demo content using ffmpeg

This docker image is targeted to provide ready streaming content along with ffmpeg.

Developed by: **Ney Moura**

Available at GitHub: [neymoura/streaming-machine](https://github.com/neymoura/streaming-machine)

Based on the
[opencoconut/ffmpeg](https://hub.docker.com/r/opencoconut/ffmpeg) image developed by Bruno Celeste (@brunoceleste)

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
$ docker run neymoura/streaming-machine:1.0.0 ffmpeg -re -i STREAM_FILE -c copy -f flv YOUR_STREAM_RMTP_URL
```

Big Buck Bunny:
```shell
$ docker run neymoura/streaming-machine:1.0.0 ffmpeg -re -i /streaming/videos/bbb.flv -c copy -f flv YOUR_STREAM_RMTP_URL
```

Sintel:
```shell
$ docker run neymoura/streaming-machine:1.0.0 ffmpeg -re -i /streaming/videos/sintel.flv -c copy -f flv YOUR_STREAM_RMTP_URL
```

# Using docker compose

Running one stream:
```yaml
services:
  streaming-machine:
    image: neymoura/streaming-machine:1.0.0
    entrypoint: ffmpeg -re -i /streaming/videos/sintel.flv -c copy -f flv YOUR_STREAM_RMTP_URL
```

Running two streams:
```yaml
services:
  stream-one:
    image: neymoura/streaming-machine:1.0.0
    entrypoint: ffmpeg -re -i /streaming/videos/sintel.flv -c copy -f flv YOUR_FIRST_STREAM_RMTP_URL
  stream-two:
    image: neymoura/streaming-machine:1.0.0
    entrypoint: ffmpeg -re -i /streaming/videos/bbb.flv -c copy -f flv YOUR_SECOND_STREAM_RMTP_URL
```

# Author

Ney Moura

https://github.com/neymoura