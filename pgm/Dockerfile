FROM ewized/sportbukkit

ARG PGM_URL="https://github.com/OvercastNetwork/ProjectAres.git"
ARG BUKKIT_SETTINGS_URL="https://github.com/OvercastNetwork/BukkitSettings.git"
ARG CHANNELS_URL="https://github.com/OvercastNetwork/Channels.git"

WORKDIR /tmp

RUN mkdir -p /minecraft/plugins \
    && git clone $PGM_URL \
    && cd ProjectAres \
    && mvn install -Dmaven.test.skip=true \
    && mv API/bukkit/target/api*.jar /minecraft/plugins/api.jar \
    && mv Commons/bukkit/target/commons*.jar /minecraft/plugins/commons.jar \
    && mv PGM/target/PGM*.jar /minecraft/plugins/pgm.jar \
    && cd .. \
    && git clone $BUKKIT_SETTINGS_URL \
    && cd BukkitSettings \
    && mvn install -Dmaven.test.skip=true \
    && mv target/bukkit-settings*.jar /minecraft/plugins/bukkit-settings.jar \
    && cd .. \
    && git clone $CHANNELS_URL \
    && cd Channels \
    && mvn install -Dmaven.test.skip=true \
    && mv target/Channels*.jar /minecraft/plugins/channels.jar \
    && rm -Rf /tmp \
    && rm -Rf /root/.m2/repository

WORKDIR /minecraft

VOLUME ["/minecraft/worlds"]

COPY . .
