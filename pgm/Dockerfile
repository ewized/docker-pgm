FROM ewized/sportbukkit

ARG PGM_URL="https://github.com/OvercastNetwork/ProjectAres.git"
ARG RAVEN_URL="https://github.com/OvercastNetwork/raven-minecraft.git"

WORKDIR /tmp

RUN git clone $PGM_URL \
    && cd ProjectAres \
    && mvn install \
    && cd .. \
    && git clone $RAVEN_URL \
    && cd raven-minecraft \
    && mvn install \
    && mkdir -p /minecraft/plugins \
    && rm -Rf /tmp \
    && rm -Rf /root/.m2/repository

WORKDIR /minecraft
