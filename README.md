# Docker for PGM

This contains the configurations to run PGM within Docker.
This combined with [PyCloud](https://github.com/Year4000/PyCloud) one can
recreate the entire network.

## Images

### SportBukkit

SportBukkit image contains the raw minecraft server.
The image can be found here [ewized/sportbukkit](https://hub.docker.com/r/ewized/sportbukkit/).

> docker run -it -p 25565:25565 ewized/sportbukkit

### PGM

PGM image contains the basic PGM minecraft server.
The image can be found here [ewized/pgm](https://hub.docker.com/r/ewized/pgm/).

> docker run -it -p 25565:25565 -v worlds:/minecraft/worlds ewized/pgm
