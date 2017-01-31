FROM isuper/java-oracle

RUN apt update && apt install -y \
    git \
    maven \
    rake \
  && apt clean

ARG SETTINGS_XML="https://gist.githubusercontent.com/ewized/210c8797d60c9e4f6a96be135120393e/raw/90e339f58af56418197f6bf6f4cb2630976ce9f8/settings.xml"
ARG SPORTBUKKIT_URL="https://github.com/OvercastNetwork/SportBukkit.git"
ARG GIT_EMAIL="ewized@ewized.com"
ARG GIT_USER="ewized"

ADD $SETTINGS_XML /root/.m2/settings.xml
RUN git config --global user.email "$GIT_EMAIL" && git config --global user.name "$GIT_NAME"

WORKDIR /tmp

RUN git clone "$SPORTBUKKIT_URL" \
  && cd SportBukkit \
  && rake \
  && mkdir /minecraft \
  && mv build/CraftBukkit/target/sportbukkit*.jar /minecraft/sportbukkit.jar \
  && rm -Rf /tmp \
  && rm -Rf /root/.m2/repository

WORKDIR /minecraft

EXPOSE 25565

CMD ["java", "-Xmx1G", "-jar", "sportbukkit.jar"]
