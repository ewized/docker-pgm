# Docker for PGM

This contains the configurations to run PGM within Docker.
This combined with [PyCloud](https://github.com/Year4000/PyCloud) one can
recreate the entire network.

## Images

### SportBukkit

SportBukkit image contains the raw minecraft server

> docker run -it -p 25565:25565 -v minecraft:/root ewized/sportbukkit
